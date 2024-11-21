class Salesman:
    def __init__(self, id, name):
        self.id = id
        self.name = name
        self.sales = 0

    def record_sale(self, amount):
        self.sales += amount
        return f"ID: {self.id}, Name: {self.name}, Sales: {self.sales}"

    def __str__(self):
        return f"ID: {self.id}, Name: {self.name}, Sales: {self.sales}"


class SalesmanTrackingApp:
    def __init__(self):
        self.salesmen = {}

    def add_salesman(self):
        id = input("Enter Salesman Id: ")
        if id in self.salesmen:
            print("Salesman with this ID already exists.")
            return
        name = input("Enter Salesman Name: ")
        self.salesmen[id] = Salesman(id, name)
        print("Salesman added successfully.")

    def record_sales(self):
        id = input("Enter Salesman ID: ")
        if id not in self.salesmen:
            print("Salesman not found.")
            return
        try:
            amount = float(input("Enter Sale Amount: "))
            if amount < 0:
                raise ValueError("Amount cannot be negative.")
            print(self.salesmen[id].record_sale(amount))
            print("Sales recorded successfully.")
        except ValueError as e:
            print(f"Invalid input: {e}")

    def view_salesman(self):
        id = input("Enter Salesman ID: ")
        if id not in self.salesmen:
            print("Salesman not found")
            return
        print(self.salesmen[id])

    def view_all_salesmen(self):
        if not self.salesmen:
            print("No salesmen available.")
            return
        for salesman in self.salesmen.values():
            print(salesman)

    def menu(self):
        while True:
            print("\nSalesman Tracking App")
            print("1. Add Salesman")
            print("2. Record Sales")
            print("3. View Salesman")
            print("4. View All Salesmen")
            print("5. Exit")
            choice = input("Enter your choice: ")
            if choice == "1":
                self.add_salesman()
            elif choice == "2":
                self.record_sales()
            elif choice == "3":
                self.view_salesman()
            elif choice == "4":
                self.view_all_salesmen()
            elif choice == "5":
                print("Bye")
                break
            else:
                print("Invalid input")


if __name__ == "__main__":
    app = SalesmanTrackingApp()
    app.menu()
