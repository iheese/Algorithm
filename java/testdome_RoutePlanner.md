```java
    public static boolean routeExists(int fromRow, int fromColumn, int toRow, int toColumn,
                                      boolean[][] mapMatrix) {
        boolean[][] visited = new boolean[mapMatrix.length][mapMatrix[0].length];
        return routeSearch(fromRow, fromColumn, toRow, toColumn, mapMatrix, visited);
    }

    public static boolean routeSearch(int fromRow, int fromColumn, int toRow, int toColumn,
                                      boolean[][] mapMatrix, boolean[][] visited) {
        // 맵의 범위를 넘으면 false
	if(fromRow < 0 || fromColumn < 0 || fromRow >= mapMatrix.length || fromColumn >= mapMatrix[0].length) {
            return false;
        }
	// 방문 했거나, 시작점, 도착점이 접근 불가능할 때
        if(visited[fromRow][fromColumn] || !mapMatrix[fromRow][fromColumn] || !mapMatrix[toRow][toColumn]) {
            return false;
        }
	// 도착 지점에 도착했다면 트루!
        if(fromRow == toRow && fromColumn == toColumn) {
            return true;
        }
	
	// 방문 처리
        visited[fromRow][fromColumn] = true;

	// 수많은 경우 중true를 찾자
        return routeSearch(fromRow-1, fromColumn, toRow, toColumn, mapMatrix, visited)
        || routeSearch(fromRow, fromColumn-1, toRow, toColumn, mapMatrix, visited)
        || routeSearch(fromRow+1, fromColumn, toRow, toColumn, mapMatrix, visited)
        || routeSearch(fromRow, fromColumn+1, toRow, toColumn, mapMatrix, visited);
    }
```
