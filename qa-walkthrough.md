# QA walkthrough

This document outlines the relevant files and highlights the location of the `vectorStore` used for Vault QA in the `hiaux0/obsidian-copilot` repository.

* `src/components/chat-components/ChatControls.tsx`
  * This file imports and uses the `VectorStoreManager` to refresh the vault index.
  * The `refreshVaultIndex` function calls `VectorStoreManager.getInstance().indexVaultToVectorStore()` to index the vault to the vector store.

* `src/components/chat-components/RelevantNotes.tsx`
  * This file imports and uses the `VectorStoreManager` to fetch relevant notes.
  * The `useRelevantNotes` function fetches notes using `VectorStoreManager.getInstance().getDb()`.
  * The `useHasIndex` function checks if a note has an index using `VectorStoreManager.getInstance().hasIndex(notePath)`.

* `src/components/modals/OramaSearchModal.tsx`
  * This file imports and uses the `vectorStoreManager` to get database operations.
  * The `searchButton` event listener calls `this.plugin.vectorStoreManager.getDbOps()` to get database operations and perform a search.

* `src/main.ts`
  * This file initializes the `VectorStoreManager` and sets it up for use in the plugin.
  * The `onload` function initializes `this.vectorStoreManager` with `VectorStoreManager.getInstance()`.

* `src/plusUtils.ts`
  * This file contains functions related to Copilot Plus settings.
  * The `applyPlusSettings` function calls `VectorStoreManager.getInstance().indexVaultToVectorStore()` to index the vault when applying Copilot Plus settings.

* `src/search/chunkedStorage.ts`
  * This file contains the `ChunkedStorage` class, which is used to manage chunked storage for the vector store.
  * The `saveDatabase` and `loadDatabase` functions handle saving and loading the database in chunks.

* `src/search/dbOperations.ts`
  * This file contains the `DBOperations` class, which provides various database operations for the vector store.
  * The `initializeDB`, `saveDB`, `clearIndex`, `removeDocs`, `upsert`, and other functions manage the database operations.

* `src/search/findRelevantNotes.ts`
  * This file contains functions to find relevant notes using the vector store.
  * The `findRelevantNotes` function uses `DBOperations` to search for relevant notes based on similarity scores and links.

* `src/search/hybridRetriever.ts`
  * This file contains the `HybridRetriever` class, which retrieves relevant documents using a hybrid approach.
  * The `getOramaChunks` function uses `VectorStoreManager.getInstance().getDb()` to get the database and perform searches.

* `src/search/indexOperations.ts`
  * This file contains the `IndexOperations` class, which handles indexing operations for the vector store.
  * The `indexVaultToVectorStore`, `reindexFile`, and other functions manage the indexing process.

* `src/search/searchUtils.ts`
  * This file contains utility functions for search operations.
  * The `getVectorLength`, `getAllQAMarkdownContent`, and other functions assist in managing the vector store.

* `src/search/vectorStoreManager.ts`
  * This file contains the `VectorStoreManager` class, which manages the vector store.
  * The `indexVaultToVectorStore`, `clearIndex`, `garbageCollectVectorStore`, `getIndexedFiles`, `isIndexEmpty`, `hasIndex`, and other functions provide various operations for the vector store.
