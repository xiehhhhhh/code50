# code50
package ktvdg;
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Scanner;

public class ktvdg {
    private static ArrayList<String> songList = new ArrayList<>();
    private static LinkedList<String> currentSongOrder = new LinkedList<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("欢迎来到KTV点歌系统！");
        System.out.println("指令0代表添加歌曲，指令1代表将所选歌曲置顶，指令2代表将所选歌曲提前一位，指令3代表退出该系统。");

        while (true) {
            System.out.println("请输入指令（0-3）或输入'退出'来结束程序：");
            int command = scanner.nextInt();
            scanner.nextLine();  // 消耗换行符  

            switch (command) {
                case 0:
                    System.out.println("添加歌曲：");
                    String songName = scanner.nextLine();
                    songList.add(songName);
                    currentSongOrder.add(songName);
                    System.out.println("当前歌曲列表：" + currentSongOrder);
                    break;
                case 1:
                    System.out.println("将所选歌曲置顶：");
                    songName = scanner.nextLine();
                    if (songList.contains(songName)) {
                        currentSongOrder.remove(songName);
                        currentSongOrder.addFirst(songName);
                        System.out.println("当前歌曲列表：" + currentSongOrder);
                    } else {
                        System.out.println("歌曲不存在！");
                    }
                    break;
                case 2:
                    System.out.println("将所选歌曲提前一位：");
                    songName = scanner.nextLine();
                    if (songList.contains(songName)) {
                        currentSongOrder.remove(songName);
                        currentSongOrder.add(songName);
                        System.out.println("当前歌曲列表：" + currentSongOrder);
                    } else {
                        System.out.println("歌曲不存在！");
                    }
                    break;
                case 3:
                    System.out.println("退出程序。");
                    return;  // 结束程序执行  
                default:
                    System.out.println("无效的指令！");
            }
        }
    }
}
