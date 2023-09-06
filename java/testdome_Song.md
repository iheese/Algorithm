```java

public class Song {
    private String name;
    private Song nextSong;

    public Song(String name) {
        this.name = name;
    }

    public void setNextSong(Song nextSong) {
        this.nextSong = nextSong;
    }

    public boolean isInRepeatingPlaylist() {
        Song next = this.nextSong; //지금 노래의 다음 노래
        Song next2 = next == null ? null : next.nextSong; // 다음 노래의 다음노래
	// 다음 노래의 다음 노래가 있으면
        while (next2 != null) {
 	   // 지금 노래와 다음 노래가 같거나, 다음 노래와 다음 다음 노래가 같으트루
            if (next == this || next == next2){
                return true;
		 }
            next = next.nextSong; // 이걸 통과하면재할당
            next2 = next2.nextSong;
            if (next2 != null)
                next2 = next2.nextSong;
        }
        return false;
    }

    public static void main(String[] args) {
        Song first = new Song("Hello");
        Song second = new Song("Eye of the tiger");

        first.setNextSong(second);
        second.setNextSong(first);

        System.out.println(first.isInRepeatingPlaylist());
    }
}
```
