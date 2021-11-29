import java.util.*;

class levelsgift<gift> {                                  // using generic programming for storring gifts or soft toys
    private ArrayList<gift> gifts;

    public levelsgift() {
        gifts = new ArrayList<gift>();
    }

    public void add(gift o) {
        gifts.add(o);
    }

    public gift get(int i) {
        return gifts.get(i);
    }
}


class player {                                          // taking users name
    public String name;

    public player() {
        Scanner input = new Scanner(System.in);
        name = input.nextLine();
    }
}

public class Hop_n_Win {
    public static boolean genericCalculator(Object o1, Object o2, Object o3) {          // generic calculator checking for true or false
        try {
            int a = (Integer) o1;
            int b = (Integer) o2;
            int res = (Integer) o3;
            if ((a / b) == res) return true;
            return false;
        } catch (Exception e) {
            try {
                String a = (String) o1;
                String b = (String) o2;
                String res = (String) o3;
                if ((a + b).equals(res)) return true;
                return false;
            } catch (Exception ee) {
                System.out.println("The arguments passed were neither integers nor strings");
                return false;
            }
        }
    }

    static int r1 = 2;
    static int r2 = 1;
    static String str1 = "abc";
    static String str2 = "def";
    static char c1 = 'a';
    static char c2 = 'b';

    public static void main(String[] args) throws NumberFormatException {
        HashMap<Integer, String> map = new HashMap<Integer, String>();                  // hashmap using for storing soft
        levelsgift<String> gft = new levelsgift<>();
        gft.add("Teady Bear");
        gft.add("Donald Duck");
        gft.add("Toy Car");
        gft.add("Monster Truck");
        gft.add("Spinner");
        gft.add("Fitzit Spinner");
        gft.add("Barbie Doll");
        gft.add("Spider Man");
        gft.add("Bat Man");
        gft.add("Iron Man");
        gft.add("Jerry");
        gft.add("Tom");
        gft.add("Popie");
        gft.add("Toy Helicopter");
        gft.add("Wizard");
        gft.add("Coin");
        gft.add("Pencil");
        gft.add("Pen");
        gft.add("Eraser");
        gft.add("Sharpner");

        System.out.println("Enter your player name");
        player user = new player();

        System.out.println("Hit enter to initialize the game");
        Scanner input = new Scanner(System.in);
        String in = input.nextLine();

        System.out.println("Game is ready");

        for(int i=1; i<=5; i++) {
            int min = 1;
            int max = 20;
            int tile = (int)(Math.random()*(max-min+1)+min);
            System.out.println();
            System.out.println("------>>>>   Hit enter for your " + i + " hop");
            in = input.nextLine();
            System.out.println("You landed on tile " + tile);
            if(tile == 2 || tile == 6 || tile == 8 || tile == 10 || tile == 12 || tile == 14 || tile == 16 || tile == 20) {
                String a = gft.get(tile-1);
                System.out.println("You won a "+ a + " soft toy");
                map.put(i,a);
                System.out.println();
            }else if(tile == 4 || tile == 18) {
                System.out.println("You are too energetic and zoomed past all the tiles. Muddy Puddle Splash!");
            }else {
                Scanner ss = new Scanner(System.in);
                System.out.println("Question answer round");
                System.out.println("Which question would you like to opt for\n1.Integer\n2.String");
                int inp = ss.nextInt();
                if (inp == 1) {
                    System.out.println("The 2 numbers are " + r1 + " " + r2);
                    r1++;
                    r2++;
                    System.out.println("Enter the result of subtraction");
                    try {
                        int res = ss.nextInt();
                        if (!genericCalculator((Object) (r1 - 1), (Object) (r2 - 1), res)) {
                            System.out.println("Sorry you cannot get the prize");
                        } else {
                            String b = gft.get(tile-1);
                            System.out.println("Correct answer");
                            System.out.println("You won a "+ b + " soft toy");
                            map.put(i,b);
                        }
                    } catch (Exception e) {
                        System.out.println("you did not enter a integer");
                    }
                } else if (inp == 2) {
                    String toBe1 = str1 + c1;
                    String toBe2 = str2 + c2;
                    c1++;
                    c2++;
                    System.out.println("The 2 strings are " + toBe1 + " " + toBe2);
                    System.out.println("Enter the result of concatenation");
                    ss.nextLine();
                    String res = ss.nextLine();
                    if (!genericCalculator((Object) (toBe1), (Object) (toBe2), res)) {
                        System.out.println("Sorry you cannot get the prize");
                    } else {
                        String b = gft.get(tile - 1);
                        System.out.println("Correct answer");
                        System.out.println("You won a " + b + " soft toy");
                        map.put(i,b);
                    }
                }
            }
        }
        System.out.println();
        System.out.println("Game Over\n" +
                "Soft toys won by you are:");
        System.out.println();
        for(Map.Entry m : map.entrySet()){
            System.out.println("in round "+m.getKey()+"-->"+m.getValue());
        }
    }
}





