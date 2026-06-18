# Seasonal Puzzle – Firestore structure

## Collections
- `seasonal_packs`
- `seasonal_packs/{packId}/items`

## `seasonal_packs` fields
- `title` (string)
- `subtitle` (string)
- `startDate` (Timestamp / Date)
- `endDate` (Timestamp / Date)
- `coverImageUrl` (string, optional)
- `coverAssetPath` (string, optional)
- `imageCount` (int)
- `isActive` (bool)

## `items` fields
- `dayIndex` (int)
- `title` (string)
- `imageUrl` (string, optional)
- `thumbnailUrl` (string, optional)
- `assetPath` (string, optional)
- `thumbnailAssetPath` (string, optional)
- `unlockDate` (Timestamp / Date)
- `pieceCount` (int, always 100 for seasonal puzzles)

## Storage path suggestion
- Full image: `seasonal_puzzles/{packId}/images/day_001.webp`
- Thumbnail: `seasonal_puzzles/{packId}/thumbs/day_001.webp`

## App logic notes
- Active pack: `isActive == true` AND `startDate <= today <= endDate`.
- Unlocking: based on `currentSeasonDay()` vs `dayIndex`.
- Home card uses `todayPuzzle` of the active pack.
- “Aktuális szezon” tab shows the full pack list with locks for future days.
- Seasonal puzzles are launched with a fixed 100-piece config.
