# Syntecxhub_FoodOrder_Bill_Genaretor



import java.util.Scanner;

public class RestaurantBill {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        String[] menu = new String[30];
        int[] price = new int[30];

        // 20 items
        menu[0]="Idli"; price[0]=30;
        menu[1]="Dosa"; price[1]=50;
        menu[2]="Poori"; price[2]=40;
        menu[3]="Vada"; price[3]=25;
        menu[4]="Upma"; price[4]=35;
        menu[5]="Veg Biryani"; price[5]=120;
        menu[6]="Chicken Biryani"; price[6]=180;
        menu[7]="Fried Rice"; price[7]=100;
        menu[8]="Noodles"; price[8]=90;
        menu[9]="Pizza"; price[9]=200;
        menu[10]="Burger"; price[10]=80;
        menu[11]="Sandwich"; price[11]=70;
        menu[12]="Paneer Curry"; price[12]=150;
        menu[13]="Roti"; price[13]=20;
        menu[14]="Ice Cream"; price[14]=60;
        menu[15]="Cake"; price[15]=90;
        menu[16]="Coffee"; price[16]=40;
        menu[17]="Tea"; price[17]=20;
        menu[18]="Juice"; price[18]=50;
        menu[19]="Soft Drink"; price[19]=35;

        int count = 20;
        double totalBill = 0;
        int choice;
        char more;

        
            System.out.println("\n===== MENU =====");

            for(int i=0; i<count; i++) {
                System.out.println((i+1)+". "+menu[i]+" - ₹"+price[i]);
            }

            System.out.println((count+1)+". Add Item");
            System.out.println((count+2)+". Remove Item");
         do{
            System.out.print("Enter choice: ");
            choice = sc.nextInt();

            if(choice == count+1) {

                sc.nextLine();

                System.out.print("Enter item name: ");
                menu[count] = sc.nextLine();

                System.out.print("Enter price: ");
                price[count] = sc.nextInt();

                count++;
                System.out.println("Item Added");

            }
            else if(choice == count+2) {

                System.out.print("Enter item number to remove: ");
                int remove = sc.nextInt()-1;

                if(remove>=0 && remove<count) {

                    for(int i=remove; i<count-1; i++) {
                        menu[i]=menu[i+1];
                        price[i]=price[i+1];
                    }

                    count--;
                    System.out.println("Item Removed");
                }

            }
            else if(choice>=1 && choice<=count) {

                System.out.print("Enter quantity: ");
                int quantity = sc.nextInt();

                totalBill += price[choice-1] * quantity;

                System.out.println("Current Bill = ₹"+totalBill);
            }

            System.out.print("Continue (Y/N): ");
            more = sc.next().charAt(0);

        } while(more=='Y' || more=='y');

        // GST calculation
        double gst = totalBill * 0.05; // 5%
        double finalBill = totalBill + gst;

        System.out.println("\n===== FINAL BILL =====");
        System.out.println("Subtotal = ₹" + totalBill);
        System.out.println("GST (5%) = ₹" + gst);
        System.out.println("Final Amount = ₹" + finalBill);

        sc.close();
    }
}