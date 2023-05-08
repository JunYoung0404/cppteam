### 

```

#include <iostream>
#include <vector>
#include <string>

// 상품 클래스
class Product {
public:
    Product(const std::string& name, double price) : name_(name), price_(price) {}

    std::string getName() const { return name_; }
    double getPrice() const { return price_; }

    void setName(const std::string& name) { name_ = name; }
    void setPrice(double price) { price_ = price; }

private:
    std::string name_;
    double price_;
};

// 고객 클래스
class Customer {
public:
    Customer(const std::string& name, const std::string& address) : name_(name), address_(address) {}

    std::string getName() const { return name_; }
    std::string getAddress() const { return address_; }

    void setName(const std::string& name) { name_ = name; }
    void setAddress(const std::string& address) { address_ = address; }

private:
    std::string name_;
    std::string address_;
};

// 주문 클래스
class Order {
public:
    Order(const Customer& customer, const Product& product, int quantity)
        : customer_(customer), product_(product), quantity_(quantity) {}

    Customer getCustomer() const { return customer_; }
    Product getProduct() const { return product_; }
    int getQuantity() const { return quantity_; }

    void setCustomer(const Customer& customer) { customer_ = customer; }
    void setProduct(const Product& product) { product_ = product; }
    void setQuantity(int quantity) { quantity_ = quantity; }

private:
    Customer customer_;
    Product product_;
    int quantity_;
};

int main() {
    // 상품, 고객, 주문 객체 생성 및 관리 예제
    Product product1("T-shirt", 19.99);
    Customer customer1("John Doe", "123 Main St");
    Order order1(customer1, product1, 2);

    std::cout << "Product: " << order1.getProduct().getName() << ", Price: $" << order1.getProduct().getPrice() << std::endl;
    std::cout << "Customer: " << order1.getCustomer().getName() << ", Address: " << order1.getCustomer().getAddress() << std::endl;
    std::cout << "Quantity: " << order1.getQuantity() << std::endl;

    return 0;
} 

```
