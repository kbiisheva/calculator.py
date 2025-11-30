import tkinter as tk
window = tk.Tk()
window.title("My calculator")
window.geometry("450x600")
window.resizable(False, False)
window.configure(bg = '#FFC0CB')

def plus():
    inp = number1.get()
    inp2 = number2.get()
    result = int(inp) + int(inp2)
    print(result)
    number3.insert(0, result)
def minus():
    inp = number1.get()
    inp2 = number2.get()
    result = int(inp) - int(inp2)
    print(result)
    number3.insert(0, result)
def multiply():
    inp = number1.get()
    inp2 = number2.get()
    result = int(inp) * int(inp2)
    print(result)
    number3.insert(0, result)
def share():
    try:
        inp = number1.get()
        inp2 = number2.get()
        result = int(inp) / int(inp2)
        print(result)
        number3.insert(0, result)
    except ZeroDivisionError:
        print("Нельзя делить на ноль!")
def NOD():
    a = int(number1.get())
    b = int(number2.get())
    result = 0
    while a != b:
        if a > b:
            a -= b
        else :
            b -= a
    result = a
    number3.delete(0, 'end')
    number3.insert(0, result)
    return result
def NOK():
    a = int(number1.get())
    b = int(number2.get())
    nod = NOD()
    result = a * b // nod
    print(result)
    number3.delete(0, 'end')
    number3.insert(0, result)
def numbersystem16():
    spisok = []
    n = int(number1.get())
    radix = 16
    symbol = ['A', 'B', 'C', 'D', 'E', 'F']
    while n > 0:
        ostatok = n % radix
        if ostatok > 9:
            spisok.append(str(symbol[ostatok - 10]))
        else:
            spisok.append(str(ostatok))
        n = n // radix
    spisok.reverse()
    result = "".join(spisok)
    number3.insert(0, result)
def ss2():
    n = int(number1.get())
    radix = 2
    spisok = []
    if n == 0:
        return 0
    result = ""
    while n > 0:
        spisok.append(str(n % radix))
        n = n // radix
    result1 = "".join(reversed(spisok))
    number3.insert(0, result1)

def numsys1016():
    n = number1.get()
    radix = 16
    symbol = ['A', 'B', 'C', 'D', 'E', 'F']
    result = 0
    degree = 0
    for i in reversed(n):
        if i in symbol:
            i = symbol.index(i) + 10
        else:
            i += int(i)

        result += i * radix ** degree
        degree += 1
    print(result)
    number3.insert(0, result)
def degree (n, stepen):
    x = n ** stepen
    return x
print(degree(2, 4))

button_add = tk.Button(window, text="+", fg="white", bg="#FF69B4", width=8, height=1, font=("Arial", 20), command=plus)
button_add.place(x=60, y=150)
button_add2 = tk.Button(window, text="-", fg="white", bg="#FF69B4", width=8, height=1, font=("Arial", 20), command=minus)
button_add2.place(x=225, y=150)
button_add = tk.Button(window, text="*", fg="white", bg="#FF69B4", width=8, height=1, font=("Arial", 20), command=multiply)
button_add.place(x=60, y=220)
button_add2 = tk.Button(window, text="/", fg="white", bg="#FF69B4", width=8, height=1, font=("Arial", 20), command=share)
button_add2.place(x=225, y=220)
button_add3 = tk.Button(window, text="In 2ns", fg="white", bg="#DB7093", width=5, height=1, font=("Arial", 20), command=ss2)
button_add3.place(x=55, y=300)
button_add4 = tk.Button(window, text="In 8ns", fg="white", bg="#DB7093", width=5, height=1, font=("Arial", 20))
button_add4.place(x=180, y=300)
button_add5 = tk.Button(window, text="In 12ns", fg="white", bg="#DB7093", width=5, height=1, font=("Arial", 20))
button_add5.place(x=305, y=300)
button_add6 = tk.Button(window, text="In 16ns", fg="white", bg="#DB7093", width=8, height=1, font=("Arial", 20), command=numbersystem16)
button_add6.place(x=70, y=365)
button_add7 = tk.Button(window, text="from 16 to 10ns", fg="white", bg="#DB7093", width=10, height=1, font=("Arial", 23), command=numsys1016)
button_add7.place(x=230, y=365)
button_add8 = tk.Button(window, text="NODE", fg="white", bg="#DB7093", width=7, height=1, font=("Arial", 20), command=NOD)
button_add8.place(x=245, y=435)
button_add9 = tk.Button(window, text="NOC", fg="white", bg="#DB7093", width=7, height=1, font=("Arial", 20), command=NOK)
button_add9.place(x=70, y=435)
number1 = tk.Entry(window, bg="#FFB6C1", fg="white", width=18, font=("Arial", 20))
number1.place(x=75, y=20)
number2 = tk.Entry(window, bg="#FFB6C1", fg="white", width=18, font=("Arial", 20))
number2.place(x=75, y=80)
number3 = tk.Entry(window, bg="#FFB6C1", fg="white", width=10, font=("Arial", 35))
number3.place(x=75, y=500)


window.mainloop()
