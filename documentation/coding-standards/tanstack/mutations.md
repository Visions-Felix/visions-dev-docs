# Tanstack Query: Handling Mutations

## Mutations in Tanstack Query

### Creating a Mutation Hook

To handle resource-specific mutations, create a custom hook that encapsulates the mutation logic. Here's an example of how to create a custom hook for adding a new post.

```tsx
// File: useAddPost.ts

import { useMutation, useQueryClient } from '@tanstack/react-query';
import { addPost } from '../api/posts.api';

const useAddPost = () => {
    const queryClient = useQueryClient();

    return useMutation(addPost, {
        // Optional onSuccess callback
        onSuccess: (newPost) => {
            // Invalidate and refetch
            queryClient.invalidateQueries(['posts']);
            // Optionally update the cache manually
            queryClient.setQueryData(['posts', newPost.id], newPost);
        },
    });
};

export default useAddPost;
```

### Using the Mutation Hook

You can use the custom hook in your components to trigger the mutation.

```tsx
import useAddPost from './useAddPost';

const AddPostComponent = () => {
    const addPostMutation = useAddPost();

    const handleAddPost = async () => {
        try {
            await addPostMutation.mutateAsync({ title: 'New Post', content: 'This is a new post.' });
        } catch (error) {
            console.error('Error adding post:', error);
        }
    };

    return (
        <div>
            <button onClick={handleAddPost}>Add Post</button>
            {addPostMutation.isLoading && <p>Adding post...</p>}
            {addPostMutation.isError && <p>Error adding post: {addPostMutation.error.message}</p>}
            {addPostMutation.isSuccess && <p>Post added successfully!</p>}
        </div>
    );
};
```

### Updating the Cache After a Mutation

Manually updating the cache after a mutation can prevent the need to re-fetch data. This can be done using the `queryClient.setQueryData` method.

```tsx
// After a new post is added
queryClient.setQueryData(['posts', newPost.id], newPost);
```

You can also use a function to update the old data immutably.

```tsx
queryClient.setQueryData(['posts'], (oldData) => {
    return [...oldData, newPost];
});
```

### Handling Optimistic Updates

Optimistic updates allow you to update the UI before the mutation is completed, providing a smoother user experience.

```tsx
const useOptimisticAddPost = () => {
    const queryClient = useQueryClient();

    return useMutation(addPost, {
        onMutate: async (newPost) => {
            await queryClient.cancelQueries(['posts']);
            const previousPosts = queryClient.getQueryData(['posts']);
            queryClient.setQueryData(['posts'], (old) => [...old, newPost]);
            return { previousPosts };
        },
        onError: (err, newPost, context) => {
            queryClient.setQueryData(['posts'], context.previousPosts);
        },
        onSettled: () => {
            queryClient.invalidateQueries(['posts']);
        },
    });
};
```

### Invalidating Queries

Invalidating a query triggers a re-fetch. To avoid invalidating all queries with a similar key, you can pass an options argument with `{exact: true}`.

```tsx
queryClient.invalidateQueries(['posts'], { exact: true });
```

### Pagination and Infinite Scrolling

For paginated or infinite scrolling data, use `useQuery` with pagination parameters or `useInfiniteQuery`.

#### Pagination

```tsx
const { status, error, data, isPreviousData } = useQuery({
    queryKey: ['posts', { page, limit }],
    keepPreviousData: true,
    queryFn: () => getPosts({ page, limit }),
});
```

#### Infinite Scrolling

```tsx
const { status, error, data, isFetchingNextPage, hasNextPage, fetchNextPage } = useInfiniteQuery({
    queryKey: ['posts', 'infinite'],
    getNextPageParam: (prev) => prev.nextPage,
    queryFn: ({ pageParam = 1 }) => getPostsPaginated(pageParam),
});
```

### Prefetching Queries

You can prefetch queries using the `queryClient.prefetchQuery` method.

```tsx
queryClient.prefetchQuery(['posts'], getPosts);
```

## Summary

Mutations in Tanstack Query are powerful for handling data changes in your application. By creating custom hooks for mutations, managing query keys appropriately, and using advanced features like optimistic updates and cache manipulation, you can build efficient and user-friendly applications. Follow these conventions and best practices to ensure a maintainable and scalable codebase.