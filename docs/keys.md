# Keys

Keys help identify which nodes were added, changed or removed from a list when a view is rendered. A key must be unique among sibling-nodes.

```jsx
const ImageGallery = images =>
  <ul>
    {images.map(({ hash, url, description }) =>
      <li key={hash}>
        <img src={url} alt={description} />
      </li>
    )}
  </ul>
```

By setting the `key` property on a virtual node, you declare that the node should correspond to a particular DOM element. This allow us to re-order the element into its new position, if the position changed, rather than risk destroying it.

Don't use an array index as key, if the index also specifies the order of siblings. If the position and number of items in a list is fixed, it will make no difference, but if the list is dynamic, the key will change every time the tree is rebuilt.

```jsx
const PlayerList = players =>
  <ul>
    {players
      .slice()
      .sort((player, nextPlayer) => nextPlayer.score - item.score)
      .map(player =>
        <li key={player.username} class={player.isAlive ? "alive" : "dead"}>
          <PlayerCard {...player} />
        </li>
      )}
  </ul>
```
