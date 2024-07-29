# Codsoft--task--1
A To-Do List application is a useful project that helps users manage and organize their tasks efficiently. This project aims to create a command-line or GUI-based application using Python, allowing users to create, update, and track their to-do lists
from tkinter import *
from tkinter import messagebox

def newTask():
    task = taskentry.get()
    if task != "":
        lb.insert(END, task)
        taskentry.delete(0, "end")
    else:
        messagebox.showwarning("warning", "Please enter some task.")

def deleteTask():
    lb.delete(ANCHOR)
    
v = Tk()
v.geometry('500x450+500+150')
v.title("TO-DO LIST")
v.resizable(0,0)
v.config(bg="grey")


frame = Frame(v)
frame.pack(pady=15)

lb = Listbox(
    frame,
    width=25,
    height=6,
    font=("ariel", 20),
    bd=0,
    fg="green",
    highlightthickness=5,
    selectbackground="red"
)
lb.pack(side='left',fill=BOTH)

task_list = [
    "prepare report",
    "submit project",
    "complete assignment",
    "read 10 pages",
    "workout"
    ]

for item in task_list:
    lb.insert(END, item)

sb = Scrollbar(frame)
sb.pack(side=RIGHT, fill=BOTH)

lb.config(yscrollcommand=sb.set)
sb.config(command=lb.yview)

x=StringVar()

taskentry = Entry(
    v,text="x",
    font=('helvetica', 24)
    )

taskentry.pack(pady=20)

button_frame = Frame(v)
button_frame.pack(pady=20)

add_button = Button(
    button_frame,
    text="Add Task",
    font=("helvetica 15 italic"),
    bg="red",
    padx=20,
    pady=10,
    command=newTask
)
add_button.pack(fill=BOTH, expand=True, side=LEFT)

del_button = Button(
    button_frame,
    text="Delete Task",
    font=("helvetica 15 italic"),
    bg="green",
    padx=20,
    pady=10,
    command=deleteTask
)
del_button.pack(fill=BOTH, expand=True, side=LEFT)
v.mainloop()
