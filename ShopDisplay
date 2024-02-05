// building a amazon-like shopping shelf to display merchandises and modify stocks based on customer consumptions
#include <iostream>
#include <vector>
#include <string>
#include <unordered_map>

class AmazonShopDisplay {
public:
    struct Product {
        std::string name;
        double price;
        int stock;

        Product(const std::string& name, double price, int stock)
            : name(name), price(price), stock(stock) {}
    };

    void addProduct(const std::string& name, double price, int stock) {
        products.push_back(Product(name, price, stock));
    }

    void displayProducts() const {
        std::cout << "Available Products:\n";
        for (const auto& product : products) {
            std::cout << "Name: " << product.name
                      << ", Price: $" << product.price
                      << ", Stock: " << product.stock << std::endl;
        }
    }

    int getStock(const std::string& productName) const {
        for (const auto& product : products) {
            if (product.name == productName) {
                return product.stock;
            }
        }
        return -1; // Indicates product not found
    }

    bool purchase(const std::string& productName, int quantity) {
        for (auto& product : products) {
            if (product.name == productName && product.stock >= quantity) {
                product.stock -= quantity;
                std::cout << "Purchased " << quantity << " of " << productName << std::endl;
                return true; // Purchase successful
            }
        }
        return false; // Purchase failed (product not found or insufficient stock)
    }

private:
    std::vector<Product> products;
};

int main() {
    AmazonShopDisplay shop;
    shop.addProduct("Book: C++ Concurrency in Action", 49.99, 10);
    shop.addProduct("Echo Dot", 29.99, 100);

    shop.displayProducts();

    std::cout << "\nStock for Echo Dot: " << shop.getStock("Echo Dot") << std::endl;

    if (shop.purchase("Echo Dot", 2)) {
        std::cout << "Purchase successful." << std::endl;
    } else {
        std::cout << "Purchase failed." << std::endl;
    }

    shop.displayProducts(); // Display updated stock levels

    return 0;
}
