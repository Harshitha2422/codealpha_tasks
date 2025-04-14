
import tkinter as tk
from tkinter import messagebox
def fibonacci(n):
 '''Generate Fibonocci sequence upto Nth number '''
 if n<0:
     messagebox.showerror("Input error","Please enter a positive integer")
     return[]
 fib_sequence=[0,1]
 for i in range(2,n):
     fib_sequence.append(fib_sequence[-1]+fib_sequence[-2])
 return fib_sequence[:n]

def format_fibonacci_sequence(fib_sequence):
    ''' formatted Fibonacci sequence for display'''
    formatted_sequence=[]
    for i in range(2,len(fib_sequence)):
        formatted_sequence.append(f"{fib_sequence[i-2]}+{fib_sequence[i-1]} = {fib_sequence[i]}")
    return "\n".join(formatted_sequence)
def display_fibonacci_sequence():
    '''Display Fibonacci sequence up to user specified number in the window'''
    try:
        n=int(entry.get())
        fib_sequence=fibonacci(n)
        if not fib_sequence:
            return
        formatted_sequence=format_fibonacci_sequence(fib_sequence)
        result_text.delete(1.0,tk.END)
        result_text.insert(tk.END,formatted_sequence)
    except ValueError:
        messagebox.showerror("Input error","please enter a valid integer")

#create a window

window=tk.Tk()
window.resizable(0,0)
window.title("FIBONACCI SEQUENCE")
# create  a label and entry to get user input
input_label=tk.Label(window,text="Enter the number of terms:")
input_label.pack()
entry=tk.Entry(window)
entry.pack()
#create a button to generate and display the fibonacci sequence
generate_btn=tk.Button(window,text="generate",command=display_fibonacci_sequence)
generate_btn.pack()


frame=tk.Frame(window)
frame.pack()
#create a text widget to display the sequence
result_text=tk.Text(frame,height=20,width=50,wrap=tk.WORD)
result_text.pack(side=tk.LEFT,fill=tk.BOTH,expand=True)

#create scrollbar
scrollbar=tk.Scrollbar(frame,command=result_text.yview)
scrollbar.pack(side=tk.RIGHT, fill=tk.Y)
result_text.config(yscrollcommand=scrollbar.set)

window.mainloop()












        
