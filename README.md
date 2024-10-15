import java.time.LocalDate;
import java.time.format.DateTimeFormatter;
import java.time.format.DateTimeParseException;
import java.util.Scanner;

public class DateComparison {
    
    public static LocalDate inputDate(Scanner scanner, String prompt) {
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd.MM.yyyy");
        while (true) {
            System.out.print(prompt);
            String dateInput = scanner.nextLine();
            try {
                return LocalDate.parse(dateInput, formatter);
            } catch (DateTimeParseException e) {
                System.out.println("Неправильний формат дати. Спробуйте ще раз. Формат дати: день.місяць.рік");
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        LocalDate date1 = inputDate(scanner, "Введіть першу дату (дд.мм.рррр): ");
        LocalDate date2 = inputDate(scanner, "Введіть другу дату (дд.мм.рррр): ");

        if (date1.isBefore(date2)) {
            System.out.println("Перша дата " + date1.format(DateTimeFormatter.ofPattern("dd.MM.yyyy")) + " раніша за другу " + date2.format(DateTimeFormatter.ofPattern("dd.MM.yyyy")) + ".");
        } else if (date1.isAfter(date2)) {
            System.out.println("Перша дата " + date1.format(DateTimeFormatter.ofPattern("dd.MM.yyyy")) + " пізніша за другу " + date2.format(DateTimeFormatter.ofPattern("dd.MM.yyyy")) + ".");
        } else {
            System.out.println("Дати однакові.");
        }

        scanner.close();
    }
}
