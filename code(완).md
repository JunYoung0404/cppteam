## 코드
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

	cout << "고객명을 입력하세요: ";
    getline(cin, customerName);
    cout << "주소를 입력하세요: ";
    getline(cin, customerAddress);
    
    cout << "상품명을 입력하세요: ";
    getline(cin, productName);
    cout << "가격을 입력하세요: ";
    cin >> productPrice;
    cin.ignore(32767, '\n'); // cin 버퍼 비우기

    cout << "주문 수량을 입력하세요: ";
    cin >> orderQuantity;
    cin.ignore(32767, '\n');

    Product product(productName, productPrice);
	Customer customer(customerName, customerAddress);
	Order order(customer, product, orderQuantity);

	cout << "=====================\n";
	cout << "현재 주문 내역: " << endl;
	cout << "상품명: " << product.getName() << endl;
	cout << "가격: " << product.getPrice() << endl;
	cout << "주문 수량: " << orderQuantity << endl;
	cout << "고객명: " << customer.getName() << endl;
	cout << "고객 주소: " << customer.getAddress() << endl;
	cout << "=====================\n";

// 상품 추가 예제
	while(1){
		printf("================\n1.상품추가\n2.상품제거\n3.고객정보변경\n4. 출력\n================");
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
			} 
		}
		
		if(menu == "2"){
			cout << "상품을 삭제하시겠습니까?(y/n)";
			cin >>action; 
			cin.ignore(32767, '\n');
			while(action == "y"){
				cout << "삭제할  상품명을 입력하세요: ";
				getline(cin,productName);
		   		order.removeProduct(productName);
				cout << "더 삭제하시겠습니까? (y/n) ";
				cin >> action;
				cin.ignore(32767, '\n');
				if(action != "y" && action != "n"){
			    	printf("y 또는 n 를 입력해 주세요\n");
					cout << "더 삭제하시겠습니까? (y/n) ";
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
			cout << "=====================\n";
			cout << "고객명: " << customer.getName() << endl;
			cout << "고객 주소: " << customer.getAddress() << endl;
			cout << "상품 리스트: " << endl;
			const vector<Product>& productList = order.getProducts();
			for (int i = 0; i < productList.size(); ++i) {
			    cout << i+1 << "번 주문 " << productList[i].getName() << " - 가격 : " << productList[i].getPrice() <<"원"<< endl;
			}
			cout << "=====================\n";
			continue;
		}
	}
}
~~~

