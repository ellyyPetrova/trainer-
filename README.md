# trainer-
Practice on the C++ classes 

#include <iostream>
#include <string>

using namespace std;

class Rune
{
private:
	int intellect;
	int speed;
	int power;

public:
	Rune()
	{
		intellect = 10;
		speed = 10;
		power = 5;

	}

	Rune(int _intellect, int _speed, int _power)
	{
		intellect = _intellect;
		speed = _speed;
		power = _power;
	}

	Rune(Rune const &one)
	{
		intellect = one.intellect;
		speed = one.speed;
		power = one.power;
	}

	int getIntellect()
	{
		return intellect;
	}
	int getSpeed()
	{
		return speed;
	}
	int getPower()
	{
		return power;
	}

	void setIntellect(int _intellect)
	{
		intellect = _intellect;
	}
	void setSpeed(int _speed)
	{
		speed = _speed;
	}
	void setPower(int _power)
	{
		power = _power;
	}

	void print()
	{
		cout << "Intellect = " << intellect << endl;
		cout << "Speed = " << speed << endl;
		cout << "Power = " << power << endl;
	}
};


class Inventory {
private:
	Rune * runes;
	int current;
	int capacity;
public:
	Inventory()
	{
		runes = new Rune[capacity];
		current = 0;
		capacity = 10;
	}

	void copy(Inventory const &other)
	{
		current = other.current;
		capacity = other.capacity;
		runes = new Rune[capacity];

		for (int i = 0; i < current; i++) {
			runes[i] = other.runes[i];
		}
	}
	Inventory(Inventory const &other)
	{
		copy(other);
	}
	~Inventory() {
		delete[]runes;
	}

	void resize(Rune *helper) {
		helper = new Rune[capacity];

		for (int i = 0; i < capacity; i++)
			runes[i] = helper[i];

		delete[] runes;

		capacity += 10;
		runes = new Rune[capacity];

		for (int i = 0; i < current; i++)
			runes[i] = helper[i];

		delete[] helper;
	}

	void add(Rune const &one) {
		if (current == capacity) {
			resize(runes);
		}
		runes[current] = one;
		current++;
	}

	void remove() {
		Rune * helper;
		helper = new Rune[capacity];

		current--;

		for (int i = 0; i < current; i++) {
			helper[i] = runes[i];
		}
		delete[] runes;

		runes = new Rune[capacity];

		for (int i = 0; i < current; i++) {
			runes[i] = helper[i];
		}
	}

	Inventory& operator=(Inventory const &other)
	{
		if (this != &other) {
			delete[] runes;
			copy(other);
		}
		return *this;
	}



	void print() {
		for (int i = 0; i < capacity; i++) {
			cout << "Runes are: " << runes << endl;
			runes[i].print();
		}
	}
};


class Student {
private:
	char *name;
	double grade;
public:
	Student() {
		name = NULL;
		grade = 4;
	}

	Student(char *name, double grade) {
		this->name = new char[strlen(name) + 1];
		strcpy_s(this->name, sizeof this->name, name);
		this->grade = grade;
	}

	~Student()
	{
		delete[] name;
	}

	Student(Student const& other) {
		this->name = new char[strlen(other.name) + 1];
		strcpy_s(this->name, sizeof this->name, other.name);
		this->grade = other.grade;
	}

	Student& operator=(Student const &other)
	{
		if (this != &other)
		{
			delete[] name;
			this->name = new char[strlen(other.name) + 1];
			strcpy_s(this->name, sizeof this->name, other.name);
			this->grade = other.grade;
		}
		return *this;
	}

	~Student()
	{
		delete[] name;
	}
};


class Fraction {
private:
	int number;
	int denom;
public:
	Fraction() {
		number = 1;
		denom = 1;
	}

	Fraction(int _number, int _denom) {
		number = _number;
		denom = _denom;
	}

	int getNumbder() {
		return number;
	}

	int getDenom() {
		return denom;
	}

	void setNumber(int _number) {
		number = _number;
	}

	void setDenom(int _denom) {
		denom = _denom;
	}

	int gcd(Fraction result) {
		while (result.number != result.denom)
			if (result.number > result.denom)
				result.number -= result.denom;
			else
				result.denom -= result.number;
		return result.number;
	}

	Fraction& operator=(Fraction const &other) {
		if (this != &other)
		{
			this->number = other.number;
			this->denom = other.denom;
		}
		return *this;
	}

	Fraction operator+(Fraction const& other) {
		return Fraction((number*other.denom + denom * other.number), denom*other.denom);
	}

	Fraction operator+(Fraction const& other) {
		return Fraction((number*other.denom - denom * other.number), denom*other.denom);
	}


	Fraction operator*(const Fraction& other) {
		int x, y;
		x = number * other.number;
		y = denom * other.denom;
		return Fraction(x, y);
	}

	Fraction operator/(const Fraction& other) {
		int x, y;
		x = number * other.denom;
		y = denom * other.number;
		return Fraction(x, y);
	}

	friend ostream& operator<<(ostream& out, Fraction& frac) {
		out << frac.number << "/" << frac.denom << endl;
		return out;
	}

	friend istream& operator>>(istream& in, Fraction& frac) {
		in >> frac.number;
		in >> frac.denom;
		return in;
	}

	Fraction(Fraction const &other) {
		number = other.number;
		denom = other.denom;
	}
};


class String {
private:
	char *content;
	int position;

public:
	String() {
		content = NULL;
		position = 1;
	}
	
	String(char *_content, int _position) {
		this->content = new char[strlen(content) + 1];
		strcpy_s(this->content, sizeof this->content, content);
		this->position = _position;
	}

	String& operator=(String const &other) {
		if (this != &other)
		{
			delete[] content;
			this->content = new char[strlen(other.content) + 1];
			strcpy_s(this->content, sizeof this->content, other.content);
			this->position = other.position;
		}
	}
	
	String& operator+(String& const other) {
		char*helper;

	}

	char* getContent() const {
		return content;

	}

	friend ostream& operator<<(ostream& out, String& other) {
		for (int i = 0; i < str.len(); i == ) out << sr.content[i];
		return out;
	}

	~String()
	{
		delete[] content;
	}
};


class Time {
	int hours;
	int minutes;

public:

	Time() {
		hours = 0;
		minutes = 0;
	}

	Time(int h, int m) {
		if (h >= 0 && h<24 && m >= 0 && m<60) {
			hours = h;
			minutes = m;
		}
		else {
			cout << "Invalid data!";
			hours = 0;
			minutes = 0;
		}
	}

	Time(Time const &other) {
		this->hours = other.hours;
		this->minutes = other.minutes;
	}

	void setHours(int h) {
		if (h >= 0 && h<24) hours = h;
	}

	void setMinutes(int m) {
		if (m >= 0 && m<60) minutes = m;
	}

	void print() {
		cout << hours << ":" << minutes << endl;
	}

	Time operator+(const Time &other) {

		int mins = minutes, h = hours;
		mins += other.minutes;

		if (mins >= 60) {
			mins -= 60;
			h++;
		}

		h += other.hours;

		if (h >= 24) h -= 24;

		return Time(h, mins);

	}

	Time operator-(const Time &other) {

		int mins = minutes, h = hours;
		mins -= other.minutes;

		if (mins<0) {
			mins += 60;
			h--;
		}

		h -= other.hours;

		if (h<0) h += 24;

		return Time(h, mins);

	}

	friend ostream& operator<<(ostream& out, Time t) {
		out << t.hours << ":" << t.minutes;
		return out;
	}

	friend istream& operator>>(istream& in, Time t) {

		cout << "Enter hours:";
		in >> t.hours;
		cout << "Enter minutes:";
		in >> t.minutes;

		return in;

	}
};


template<typename T>
class Stack {
	int size;                                        //LIFO-last int first out
	int current;                                     //push-in
	T*container;                                  //pop-out
public:
	void copy(Stack const &other )
	{
		current = other.current;
		size = other.size;
		container = new T[size];

		for (int i = 0; i < current; i++) {
			container[i] = other.container[i];
		}
	}

	void resize() {
		int *helper;
		helper = new int[size];

		for (int i = 0; i < current; i++)
			helper[i] = container[i];

		delete[] container;

		size += 1;
		container = new T[size];

		for (int i = 0; i < current; i++)
			container[i] = helper[i];

		delete[] helper;
	}

	void erase()
	{
		delete[]container;
	}

	Stack () {
		size = 10;
		current = 0;
		container = new T[size];
	}

	Stack (int _size, int _current, int *_container)
	{
		size = _size;
		current = _current;
		container = new T[size];
	}

	int getSize(int _size)
	{
		return current;
	}

	int push(int item)
	{
		if (size == current) resize();
		container[current] = item;
		current++;
	}

	int pop(int num)
	{
		if (current == 0)
			cout << "Stack is Empty!" << endl;
		else
			current++;
	}

	int top()
	{
		return container[current-1];
	}

	bool empty()
	{
		if (current == -1)
			return true;
		else
			return false;
	}

	~Stack()
	{
		delete[]container;
	}

	Stack& operator=(Stack const &other)
	{
		if (this != &other) {
			delete[] container;
			copy(other);
		}
		return *this;
	}

	void swap(int i1, int i2) {

		if (i1 >= 0 && i2 >= 0 && i1 < current && i2 < current) {
			int helper = container[i1];
			container[i1] = container[i2];
			container[i2] = helper;
		}
	}



};
//FIFO-First in firs out



template<typename T>                       //	Queue <int> queue;--sintaxys
class Queue {
	int size;
	int current;
	T *container;
public:
	void copy(Queue const &other)
	{
		current = other.current;
		size = other.size;
		container = new T[size];

		for (int i = 0; i < current; i++) {
			container[i] = other.container[i];
		}
	}

	void resize() {
		int *helper;
		helper = new T[size];

		for (int i = 0; i < current; i++)
			helper[i] = container[i];

		delete[] container;

		size += 1;
		container = new T[size];

		for (int i = 0; i < current; i++)
			container[i] = helper[i];

		delete[] helper;
	}

	void erase()
	{
		delete[]container;
	}
	Queue() {
		size = 10;
		current = 0;
		container = new T[size];
	}

	Queue(int _size, int _current, T *_container)
	{
		size = _size;
		current = _current;
		container = new T[size];
	}


	Queue& operator=(Queue const &other)
	{
		if (this != &other) {
			delete[] container;
			copy(other);
		}
		return *this;
	}

	bool empty()
	{
		if (current == 0)
			return true;
		else
			return false;
	}

	~Queue() {
		delete[]container;
	}
	
	int getSize()
	{
		return current;
	}

	int front() {
		return container[0];
	}

	int back() {
		return container[current-1];
	}

	int push(int item)
	{
		if (size == current) resize();
		container[current] = item;
		current++;
	}

	int pop(int num)
	{
		for (int i = 0; i < current - 1; i++)
			container[i] = container[i + 1];
			current--;
	}

	void swap(int i1, int i2) {

		if (i1 >= 0 && i2 >= 0 && i1 < current && i2 < current) {
			int helper = container[i1];
			container[i1] = container[i2];
			container[i2] = helper;
		}
	}

};






class Person {
	char *name;
	int ID;
public:
	Person() {
		name = NULL;
		ID = 0;
	}

	Person(char *_name, int _ID) {
		this->name = new char[strlen(name) + 1];
		strcpy_s(this->name, sizeof this->name, name);
		this->ID = ID;
	}

	~Person() {
		delete[]name;
	}

	Person& operator=(Person const other) {
		if (this != &other)
		{
			delete[] name;
			this->name = new char[strlen(other.name) + 1];
			strcpy_s(this->name, sizeof this->name, other.name);
			this->ID = other.ID;
		}
		return *this;
	}

	void print(){
		cout << "The name of the person is ";
		if (name != NULL)
		{
			for (int i = 0; i <= strlen(name); i++)
				cout << name[i];
		}
		else
			cout << "No name";
		cout << endl;
		cout	<< "His ID is " << ID<< endl;
	}
};

class Student : Person {
	double grade;
public:
	Student() : Person() {
		grade = 2;
	}

	Student(char *_name, int _ID, double _grade) : Person(_name, _ID) {
		grade = _grade;
	}

	Student& operator=(Student const& other) {
		if (this != &other) {
			Person::operator=(other);
			grade = other.grade;
		}
		return*this;
	}

	void print() {
		Person::print();
		cout << "The grade of the student is " << grade << endl;
	}
};
