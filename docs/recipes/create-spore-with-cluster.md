---
sidebar_position: 5
---

# Create Spore With Cluster

In this recipe, you’ll learn how to tag a [Cluster](/basics/spore-101#what-is-a-cluster) when creating a [Spore](/basics/spore-101#what-is-a-spore). If you are looking to create standalone spores (spores without cluster) refer to: [Create a Spore](/recipes/create-spore).

:::caution

- You can only utilize a Cluster as a tag if it can be unlocked by you to use. 
- You cannot tag a Spore after its creation; you'll need to destroy and then tag it during the creation process.
- Each Spore can be associated with only one Cluster.

:::

Your target cluster can be either a [public cluster](/recipes/create-private-cluster) or a [private cluster](/recipes/create-private-cluster), depending on the its lock script.

![spore-in-cluster-flowchart.png](../../static/img/recipes/spore-in-cluster/flowchart.png)

## Create Spore With a Cluster

You can tag a spore with a cluster by specifying the `data.clusterId` when calling the `createSpore` API from spore-sdk:

```tsx
import { createSpore } from '@spore-sdk/core';

let { txSkeleton } = await createSpore({
  data: {
    contentType: CONTENT_MIME_TYPE,
    content: CONTENT_AS_BYTES,
    // highlight-next-line
    clusterId: CLUSTER_ID,
  },
  toLock: OWNER_LOCK,
  fromInfos: [SPONSOR_ADDRESS],
});
```

- `data.clusterId` - The ID of the cluster to be assigned to the spore. The cluster's ID is equivalent to the type script args of the cluster.

