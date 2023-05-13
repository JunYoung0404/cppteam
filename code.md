### 코드

~~~
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
    std::string productName;
    double productPrice;
    std::string customerName;
    std::string customerAddress;
    int orderQuantity;

    std::cout << "상품명을 입력하세요: ";
    std::getline(std::cin, productName);
    std::cout << "가격을 입력하세요: ";
    std::cin >> productPrice;
    std::cin.ignore(32767, '\n'); // cin 버퍼 비우기

    std::cout << "고객명을 입력하세요: ";
    std::getline(std::cin, customerName);
    std::cout << "주소를 입력하세요: ";
    std::getline(std::cin, customerAddress);

    std::cout << "주문 수량을 입력하세요: ";
    std::cin >> orderQuantity;

    Product product(productName, productPrice);
    Customer customer(customerName, customerAddress);
    Order order(customer, product, orderQuantity);

    std::cout << "상품: " << order.getProduct().getName() << ", 가격: $" << order.getProduct().getPrice() << std::endl;
    std::cout << "고객명: " << order.getCustomer().getName() << ", 주소: " << order.getCustomer().getAddress() << std::endl;
    std::cout << "주문 수량: " << order.getQuantity() << std::endl;

    return 0;
}

~~~

#### using namespace std;
~~~

#include <iostream>
#include <vector>
#include <string>

using namespace std;

// 상품 클래스
class Product {
public:
    Product(const string& name, double price) : name_(name), price_(price) {}

    string getName() const { return name_; }
    double getPrice() const { return price_; }

    void setName(const string& name) { name_ = name; }
    void setPrice(double price) { price_ = price; }

private:
    string name_;
    double price_;
};

// 고객 클래스
class Customer {
public:
    Customer(const string& name, const string& address) : name_(name), address_(address) {}

    string getName() const { return name_; }
    string getAddress() const { return address_; }

    void setName(const string& name) { name_ = name; }
    void setAddress(const string& address) { address_ = address; }

private:
    string name_;
    string address_;
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
    string productName;
    double productPrice;
    string customerName;
    string customerAddress;
    int orderQuantity;

    cout << "상품명을 입력하세요: ";
    getline(cin, productName);
    cout << "가격을 입력하세요: ";
    cin >> productPrice;
    cin.ignore(32767, '\n'); // cin 버퍼 비우기

    cout << "고객명을 입력하세요: ";
    getline(cin, customerName);
    cout << "주소를 입력하세요: ";
    getline(cin, customerAddress);

    cout << "주문 수량을 입력하세요: ";
    cin >> orderQuantity;

    Product product(productName, productPrice);
    Customer customer(customerName, customerAddress);
    Order order(customer, product, orderQuantity);

    cout << "상품: " << order.getProduct().getName() << ", 가격: $" << order.getProduct().getPrice() << endl;
    cout << "고객명: " << order.getCustomer().getName() << ", 주소: " << order.getCustomer().getAddress() << endl;
    cout << "주문 수량: " << order.getQuantity() << endl;

    return 0;
}

~~~

### 코드 설명

 이 코드는 C++을 사용하여 상품, 고객, 주문 객체를 생성하고 관리하는 예제입니다. 클래스를 사용하여 객체를 모델링하고 생성하며, 객체의 상태를 변경하기 위해 public 멤버 함수를 사용합니다.

 먼저, 상품 클래스(Product)는 상품명(name)과 가격(price)을 멤버 변수로 가지며, 생성자에서 초기화합니다. getName(), getPrice() 함수를 사용하여 상품명과 가격을 가져올 수 있습니다. setName(), setPrice() 함수를 사용하여 상품명과 가격을 변경할 수 있습니다.

 고객 클래스(Customer)는 이름(name)과 주소(address)를 멤버 변수로 가지며, 생성자에서 초기화합니다. getName(), getAddress() 함수를 사용하여 이름과 주소를 가져올 수 있습니다. setName(), setAddress() 함수를 사용하여 이름과 주소를 변경할 수 있습니다.

 주문 클래스(Order)는 고객(Customer)과 상품(Product), 수량(quantity)을 멤버 변수로 가지며, 생성자에서 초기화합니다. getCustomer(), getProduct(), getQuantity() 함수를 사용하여 고객, 상품, 수량을 가져올 수 있습니다. setCustomer(), setProduct(), setQuantity() 함수를 사용하여 고객, 상품, 수량을 변경할 수 있습니다.

 main() 함수에서는 사용자로부터 상품명, 가격, 고객명, 주소, 주문 수량을 입력받고, Product, Customer, Order 객체를 생성하여 초기화합니다. getOrder().getProduct().getName(), getOrder().getCustomer().getName()과 같은 방법으로 객체의 속성을 출력할 수 있습니다.


~~~
#include <iostream>
#include <vector>
#include <string>

using namespace std;

// 상품 클래스
class Product {
public:
    Product(const string& name, double price) : name_(name), price_(price) {}

    string getName() const { return name_; }
    double getPrice() const { return price_; }

    void setName(const string& name) { name_ = name; }
    void setPrice(double price) { price_ = price; }

private:
    string name_;
    double price_;
};

// 고객 클래스
class Customer {
public:
    Customer(const string& name, const string& address) : name_(name), address_(address) {}

    string getName() const { return name_; }
    string getAddress() const { return address_; }

    void setName(const string& name) { name_ = name; }
    void setAddress(const string& address) { address_ = address; }

private:
    string name_;
    string address_;
};

// 주문 클래스
class Order {
public:
    Order(const Customer& customer, const Product& product, int quantity)
        : customer_(customer), quantity_(quantity) {
            for (int i = 0; i < quantity; ++i) {
                products_.push_back(product);
            }
        }

    Customer getCustomer() const { return customer_; }
    const vector<Product>& getProducts() const { return products_; }

    void addProduct(const Product& product, int quantity = 1) {
        for (int i = 0; i < quantity; ++i) {
            products_.push_back(product);
        }
    }

    void removeProduct(int index, int quantity = 1) {
        if (index >= 0 && index < products_.size()) {
            if (quantity >= products_.size() - index) {
                products_.erase(products_.begin() + index, products_.end());
            } else {
                products_.erase(products_.begin() + index, products_.begin() + index + quantity);
            }
        }
    }

    void removeProduct(const string& productName, int quantity = 1) {
        int count = 0;
        for (int i = 0; i < products_.size(); ++i) {
            if (products_[i].getName() == productName) {
                if (count < quantity) {
                    products_.erase(products_.begin() + i);
                    ++count;
                    --i;
                } else {
                    break;
                }
            }
        }
    }

private:
    Customer customer_;
    vector<Product> products_;
    int quantity_;
};

int main() {
    // 상품, 고객, 주문 객체 생성 및 관리 예제
    string productName;
    double productPrice;
    string customerName;
    string customerAddress;
    int orderQuantity;
    string action;

    cout << "상품명을 입력하세요: ";
    getline(cin, productName);
    cout << "가격을 입력하세요: ";
    cin >> productPrice;
    cin.ignore(32767, '\n'); // cin 버퍼 비우기

    cout << "고객명을 입력하세요: ";
    getline(cin, customerName);
    cout << "주소를 입력하세요: ";
    getline(cin, customerAddress);

    cout << "주문 수량을 입력하세요: ";
    cin >> orderQuantity;

    Product product(productName, productPrice);
    Customer customer(customerName, customerAddress);
    Order order(customer, product, orderQuantity);

    cout << "상품: " << order.getProducts()[0].getName() << ", 가격: $" << order.getProducts()[0].getPrice() << endl;
    cout << "고객명: " << order.getCustomer().getName() << ", 주소: " << order.getCustomer().getAddress() << endl;

    while (1) {
        cout << "추가 상품을 입력하려면 '추가', 삭제하려면 '삭제', 종료하려면 '종료'를 입력하세요: ";
        cin >> action;
        cin.ignore(32767, '\n');

        if (action == "추가") {
            cout << "상품명을 입력하세요: ";
            getline(cin, productName);
            cout << "가격을 입력하세요: ";
            cin >> productPrice;
            cin.ignore(32767, '\n'); // cin 버퍼 비우기

            Product newProduct(productName, productPrice);

            cout << "상품 수량을 입력하세요: ";
            cin >> orderQuantity;
            cin.ignore(32767, '\n'); // cin 버퍼 비우기

            order.addProduct(newProduct, orderQuantity);

            cout << "상품이 추가되었습니다." << endl;
        } else if (action == "삭제") {
            if (order.getProducts().empty()) {
                cout << "삭제할 상품이 없습니다." << endl;
            } else {
                cout << "삭제할 상품의 상품명을 입력하세요: ";
                getline(cin, productName);

                cout << "삭제할 상품 수량을 입력하세요: ";
                cin >> orderQuantity;
                cin.ignore(32767, '\n'); // cin 버퍼 비우기

                order.removeProduct(productName, orderQuantity);

                cout << "상품이 삭제되었습니다." << endl;
            }
        } else if (action == "종료") {
            break;
        }
    }

    cout << "주문한 상품 목록:" << endl;
    for (int i = 0; i < order.getProducts().size(); ++i) {
        cout << i + 1 << ". 상품: " << order.getProducts()[i].getName() << ", 가격: $" << order.getProducts()[i].getPrice() << endl;
    }

    return 0;
}
~~~
마지막 수정자 : 
### 박형민이 고친 코드 
~~~
#include <iostream>
#include <vector>
#include <string>
#include <cstdlib>

using namespace std;

// Person 클래스
class Person {
public:
    Person(const string& name, const string& address) : name_(name), address_(address) {}

    string getName() const { return name_; }
    string getAddress() const { return address_; }

    void setName(const string& name) { name_ = name; }
    void setAddress(const string& address) { address_ = address; }

private:
    string name_;
    string address_;
};

// 상품 클래스
class Product : public Person {
public:
    Product(const string& name, double price) : Person("", ""), name_(name), price_(price) {}

    string getName() const { return name_; }
    double getPrice() const { return price_; }

    void setName(const string& name) { name_ = name; }
    void setPrice(double price) { price_ = price; }

	
private:
    string name_;
    double price_;
};

// 고객 클래스
class Customer : public Person {
public:
    Customer(const string& name, const string& address) : Person(name, address) {}
};

// 주문 클래스
class Order {
public:
    Order(const Customer& customer, const Product& product, int quantity)
        : customer_(customer), quantity_(quantity) {
            for (int i = 0; i < quantity; ++i) {
                products_.push_back(product);
            }
        }

    Customer getCustomer() const { return customer_; }
    const vector<Product>& getProducts() const { return products_; }

    void addProduct(const Product& product , int quantity) {
        for (int i = 0; i < quantity; ++i) {
            products_.push_back(product);
        }
    }
    
    void removeProduct(const string& productName) {
        for (int i = 0; i < products_.size(); ++i) {
            if (products_[i].getName() == productName) {
                products_.erase(products_.begin() + i);
                break;
            }
        }
    }

private:
    Customer customer_;
    vector<Product> products_;
    int quantity_;
};

int main() {
    // 상품, 고객, 주문 객체 생성 및 관리 예제
    string productName;
    double productPrice;
    string customerName;
    string customerAddress;
    int orderQuantity;
    string action;
    string menu;

    cout << "상품명을 입력하세요: ";
    getline(cin, productName);
    cout << "가격을 입력하세요: ";
    cin >> productPrice;
    cin.ignore(32767, '\n'); // cin 버퍼 비우기
    
    cout << "고객명을 입력하세요: ";
    getline(cin, customerName);
    cout << "주소를 입력하세요: ";
    getline(cin, customerAddress);

    cout << "주문 수량을 입력하세요: ";
    cin >> orderQuantity;
    cin.ignore(32767, '\n');

    Product product(productName, productPrice);
	Customer customer(customerName, customerAddress);
	Order order(customer, product, orderQuantity);

	cout << "현재 주문 내역: " << endl;
	cout << "상품명: " << product.getName() << endl;
	cout << "가격: " << product.getPrice() << endl;
	cout << "주문 수량: " << orderQuantity << endl;
	cout << "고객명: " << customer.getName() << endl;
	cout << "고객 주소: " << customer.getAddress() << endl;

// 상품 추가 예제
	while(1){
		printf("1.상품추가\n2.상품제거\n3.고객정보변경\n4. 출력\n");
		getline(cin, menu);
		
		if(menu == "1"){
			cout << "더 추가하시겠습니까? (y/n) ";
			cin >> action;
	    	if(action != "y" && action != "n"){
	    	printf("y 또는 n 를 입력해 주세요\n");
			cout << "더 추가하시겠습니까? (y/n) ";
	   		cin >> action;
	   		cin.ignore(32767, '\n');
			}
			while (action == "y") {
			    cout << "추가할 상품명을 입력하세요: ";
			    getline(cin, productName);
			    cout << "가격을 입력하세요: ";
			    cin >> productPrice;
			    cin.ignore(32767, '\n');
			    cout << "추가  수량을 입력하세요: ";
			    cin >> orderQuantity;
			
			    Product newProduct(productName, productPrice);
			    order.addProduct(newProduct,orderQuantity);
			
			    cout << "더 추가하시겠습니까? (y/n) ";
			    cin >> action;
			    if(action != "y" && action != "n"){
			    	printf("y 또는 n 를 입력해 주세요\n");
					cout << "더 추가하시겠습니까? (y/n) ";
			   		cin >> action;
			   		cin.ignore(32767, '\n');
				} 
			}
		}
		
		if(menu == "2"){
			cout << "상품을 삭제하시겠습니까?(y/n)";
			cin >>action; 
			cin.ignore(32767, '\n');
			while(action == "y"){
				cout << "삭제할  상품명을 입력하세요: ";
				getline(cin,productName);
				if (isdigit(action[0])) {
		   		order.removeProduct(productName);
				}
				cout << "더 삭제하시겠습니까? (y/n) ";
				cin >> action;
				cin.ignore(32767, '\n');
			}
		}
	
		if(menu == "3"){
			cout << "고객명을 입력하세요: ";
			getline(cin, customerName);
	    	cout << "주소를 입력하세요: ";
	    	getline(cin, customerAddress);
	    	customer.setName(customerName);
	    	customer.setAddress(customerAddress);
		}
		
		if(menu == "4"){
			cout << "고객명: " << customer.getName() << endl;
			cout << "고객 주소: " << customer.getAddress() << endl;
			cout << "상품 리스트: " << endl;
			const vector<Product>& productList = order.getProducts();
			for (int i = 0; i < productList.size(); ++i) {
			    cout << i << ". " << productList[i].getName() << " - 가격 : " << productList[i].getPrice() << endl;
			}
		}
		continue;
	}
}
~~~
마지막 수정자 : 
### 천준영이 고친 코드 
#include <iostream>
#include <vector>
#include <string>
#include <cstdlib>

using namespace std;

// Person 클래스
class Person {
public:
    Person(const string& name, const string& address) : name_(name), address_(address) {}

    string getName() const { return name_; }
    string getAddress() const { return address_; }

    void setName(const string& name) { name_ = name; }
    void setAddress(const string& address) { address_ = address; }

private:
    string name_;
    string address_;
};

// 상품 클래스
class Product : public Person {
public:
    Product(const string& name, double price) : Person("", ""), name_(name), price_(price) {}

    string getName() const { return name_; }
    double getPrice() const { return price_; }

    void setName(const string& name) { name_ = name; }
    void setPrice(double price) { price_ = price; }

	
private:
    string name_;
    double price_;
};

// 고객 클래스
class Customer : public Person {
public:
    Customer(const string& name, const string& address) : Person(name, address) {}
};

// 주문 클래스
class Order {
public:
    Order(const Customer& customer, const Product& product, int quantity)
        : customer_(customer), quantity_(quantity) {
            for (int i = 0; i < quantity; ++i) {
                products_.push_back(product);
            }
        }

    Customer getCustomer() const { return customer_; }
    const vector<Product>& getProducts() const { return products_; }

    void addProduct(const Product& product , int quantity) {
        for (int i = 0; i < quantity; ++i) {
            products_.push_back(product);
        }
    }
    
    void removeProduct(const string& productName) {
        for (int i = 0; i < products_.size(); ++i) {
            if (products_[i].getName() == productName) {
                products_.erase(products_.begin() + i);
                break;
            }
        }
    }

private:
    Customer customer_;
    vector<Product> products_;
    int quantity_;
};

int main() {
    // 상품, 고객, 주문 객체 생성 및 관리 예제
    string productName;
    double productPrice;
    string customerName;
    string customerAddress;
    int orderQuantity;
    string action;
    string menu;

    cout << "상품명을 입력하세요: ";
    getline(cin, productName);
    cout << "가격을 입력하세요: ";
    cin >> productPrice;
    cin.ignore(32767, '\n'); // cin 버퍼 비우기
    
    cout << "고객명을 입력하세요: ";
    getline(cin, customerName);
    cout << "주소를 입력하세요: ";
    getline(cin, customerAddress);

    cout << "주문 수량을 입력하세요: ";
    cin >> orderQuantity;
    cin.ignore(32767, '\n');

    Product product(productName, productPrice);
	Customer customer(customerName, customerAddress);
	Order order(customer, product, orderQuantity);

	cout << "현재 주문 내역: " << endl;
	cout << "상품명: " << product.getName() << endl;
	cout << "가격: " << product.getPrice() << endl;
	cout << "주문 수량: " << orderQuantity << endl;
	cout << "고객명: " << customer.getName() << endl;
	cout << "고객 주소: " << customer.getAddress() << endl;

// 상품 추가 예제
	while(1){
		printf("1.상품추가\n2.상품제거\n3.고객정보변경\n4. 출력\n");
		getline(cin, menu);
		
		if(menu == "1"){
			cout << "더 추가하시겠습니까? (y/n) ";
			cin >> action;
			cin.ignore(32767, '\n');
	    	if(action != "y" && action != "n"){
	    	printf("y 또는 n 를 입력해 주세요\n");
			cout << "더 추가하시겠습니까? (y/n) ";
	   		cin >> action;
	   		cin.ignore(32767, '\n');
			}
			while (action == "y") {
			    cout << "추가할 상품명을 입력하세요: ";
			    getline(cin, productName);
			    cout << "가격을 입력하세요: ";
			    cin >> productPrice;
			    cin.ignore(32767, '\n');
			    cout << "추가  수량을 입력하세요: ";
			    cin >> orderQuantity;
			
			    Product newProduct(productName, productPrice);
			    order.addProduct(newProduct,orderQuantity);
			
			    cout << "더 추가하시겠습니까? (y/n) ";
			    cin >> action;
			    cin.ignore(32767, '\n');
			    if(action != "y" && action != "n"){
			    	printf("y 또는 n 를 입력해 주세요\n");
					cout << "더 추가하시겠습니까? (y/n) ";
			   		cin >> action;
			   		cin.ignore(32767, '\n');
				} 
			}제 
		}
		
		if(menu == "2"){
			cout << "상품을 삭제하시겠습니까?(y/n)";
			cin >>action; 
			cin.ignore(32767, '\n');
			while(action == "y"){
				cout << "삭제할  상품명을 입력하세요: ";
				getline(cin,productName);
				if (isdigit(action[0])) {
		   		order.removeProduct(productName);
				}
				cout << "더 삭제하시겠습니까? (y/n) ";
				cin >> action;
				cin.ignore(32767, '\n');
				if(action != "y" && action != "n"){
			    	printf("y 또는 n 를 입력해 주세요\n");
					cout << "더 삭하시겠습니까? (y/n) ";
			   		cin >> action;
			   		cin.ignore(32767, '\n');
				} 
			}
			continue;
		}
	
		if(menu == "3"){
			cout << "고객명을 입력하세요: ";
			getline(cin, customerName);
	    	cout << "주소를 입력하세요: ";
	    	getline(cin, customerAddress);
	    	customer.setName(customerName);
	    	customer.setAddress(customerAddress);
	    	continue;
		}
		
		if(menu == "4"){
			cout << "고객명: " << customer.getName() << endl;
			cout << "고객 주소: " << customer.getAddress() << endl;
			cout << "상품 리스트: " << endl;
			const vector<Product>& productList = order.getProducts();
			for (int i = 0; i < productList.size(); ++i) {
			    cout << i << ". " << productList[i].getName() << " - 가격 : " << productList[i].getPrice() << endl;
			}
			continue;
		}
	}
}
