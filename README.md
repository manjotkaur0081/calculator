import tkinter as tk

def button_click(event):
    text = event.widget.cget("text")
    if text == "=":
        try:
            result = str(eval(screen.get()))
            screen.set(result)
        except Exception as e:
            screen.set("Error")
    elif text == "C":
        screen.set("")
    else:
        screen.set(screen.get() + text)

root = tk.Tk()
root.geometry("400x600")
root.title("Calculator")

screen = tk.StringVar()
screen.set("")

entry = tk.Entry(root, textvar=screen, font="Arial 24", bd=10, insertwidth=4, width=14, justify='right')
entry.pack()

buttons = [
    ("7", 1, 1), ("8", 1, 2), ("9", 1, 3), ("/", 1, 4),
    ("4", 2, 1), ("5", 2, 2), ("6", 2, 3), ("*", 2, 4),
    ("1", 3, 1), ("2", 3, 2), ("3", 3, 3), ("-", 3, 4),
    ("0", 4, 1), (".", 4, 2), ("=", 4, 3), ("+", 4, 4),
    ("C", 5, 1)
]

for (text, row, col) in buttons:
    button = tk.Button(root, text=text, padx=20, pady=20, font="Arial 18")
    button.grid(row=row, column=col)
    button.bind("<Button-1>", button_click)

root.mainloop()
