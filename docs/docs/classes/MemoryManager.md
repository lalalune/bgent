---
id: "MemoryManager"
title: "Class: MemoryManager"
sidebar_label: "MemoryManager"
sidebar_position: 0
custom_edit_url: null
---

Manage memories in the database.

## Constructors

### constructor

• **new MemoryManager**(`opts`): [`MemoryManager`](MemoryManager.md)

Constructs a new MemoryManager instance.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `opts` | `Object` | Options for the manager. |
| `opts.runtime` | [`BgentRuntime`](BgentRuntime.md) | The BgentRuntime instance associated with this manager. |
| `opts.tableName` | `string` | The name of the table this manager will operate on. |

#### Returns

[`MemoryManager`](MemoryManager.md)

## Properties

### runtime

• **runtime**: [`BgentRuntime`](BgentRuntime.md)

The BgentRuntime instance associated with this manager.

___

### tableName

• **tableName**: `string`

The name of the database table this manager operates on.

## Methods

### addEmbeddingToMemory

▸ **addEmbeddingToMemory**(`memory`): `Promise`\<[`Memory`](../interfaces/Memory.md)\>

Adds an embedding vector to a memory object. If the memory already has an embedding, it is returned as is.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `memory` | [`Memory`](../interfaces/Memory.md) | The memory object to add an embedding to. |

#### Returns

`Promise`\<[`Memory`](../interfaces/Memory.md)\>

A Promise resolving to the memory object, potentially updated with an embedding vector.

___

### countMemories

▸ **countMemories**(`room_id`, `unique?`): `Promise`\<`number`\>

Counts the number of memories associated with a set of user IDs, with an option for uniqueness.

#### Parameters

| Name | Type | Default value | Description |
| :------ | :------ | :------ | :------ |
| `room_id` | \`$\{string}-$\{string}-$\{string}-$\{string}-$\{string}\` | `undefined` | The room ID to count memories for. |
| `unique` | `boolean` | `true` | Whether to count unique memories only. |

#### Returns

`Promise`\<`number`\>

A Promise resolving to the count of memories.

___

### createMemory

▸ **createMemory**(`memory`, `unique?`): `Promise`\<`void`\>

Creates a new memory in the database, with an option to check for similarity before insertion.

#### Parameters

| Name | Type | Default value | Description |
| :------ | :------ | :------ | :------ |
| `memory` | [`Memory`](../interfaces/Memory.md) | `undefined` | The memory object to create. |
| `unique` | `boolean` | `false` | Whether to check for similarity before insertion. |

#### Returns

`Promise`\<`void`\>

A Promise that resolves when the operation completes.

___

### getMemories

▸ **getMemories**(`opts`): `Promise`\<[`Memory`](../interfaces/Memory.md)[]\>

Retrieves a list of memories by user IDs, with optional deduplication.

#### Parameters

| Name | Type | Default value | Description |
| :------ | :------ | :------ | :------ |
| `opts` | `Object` | `undefined` | Options including user IDs, count, and uniqueness. |
| `opts.count?` | `number` | `10` | The number of memories to retrieve. |
| `opts.room_id` | \`$\{string}-$\{string}-$\{string}-$\{string}-$\{string}\` | `undefined` | The room ID to retrieve memories for. |
| `opts.unique?` | `boolean` | `true` | Whether to retrieve unique memories only. |

#### Returns

`Promise`\<[`Memory`](../interfaces/Memory.md)[]\>

A Promise resolving to an array of Memory objects.

___

### getCachedEmbeddings

▸ **getCachedEmbeddings**(`content`): `Promise`\<`SimilaritySearch`[]\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `content` | `string` |

#### Returns

`Promise`\<`SimilaritySearch`[]\>

___

### removeAllMemories

▸ **removeAllMemories**(`room_id`): `Promise`\<`void`\>

Removes all memories associated with a set of user IDs.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `room_id` | \`$\{string}-$\{string}-$\{string}-$\{string}-$\{string}\` | The room ID to remove memories for. |

#### Returns

`Promise`\<`void`\>

A Promise that resolves when the operation completes.

___

### removeMemory

▸ **removeMemory**(`memoryId`): `Promise`\<`void`\>

Removes a memory from the database by its ID.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `memoryId` | \`$\{string}-$\{string}-$\{string}-$\{string}-$\{string}\` | The ID of the memory to remove. |

#### Returns

`Promise`\<`void`\>

A Promise that resolves when the operation completes.

___

### searchMemoriesByEmbedding

▸ **searchMemoriesByEmbedding**(`embedding`, `opts`): `Promise`\<[`Memory`](../interfaces/Memory.md)[]\>

Searches for memories similar to a given embedding vector.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `embedding` | `number`[] | The embedding vector to search with. |
| `opts` | `Object` | Options including match threshold, count, user IDs, and uniqueness. |
| `opts.count?` | `number` | The maximum number of memories to retrieve. |
| `opts.match_threshold?` | `number` | The similarity threshold for matching memories. |
| `opts.room_id` | \`$\{string}-$\{string}-$\{string}-$\{string}-$\{string}\` | The room ID to retrieve memories for. |
| `opts.unique?` | `boolean` | Whether to retrieve unique memories only. |

#### Returns

`Promise`\<[`Memory`](../interfaces/Memory.md)[]\>

A Promise resolving to an array of Memory objects that match the embedding.
