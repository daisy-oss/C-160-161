from tkinter import*
from PIL import ImageTk, Image
from tkinter import filedialog
import os

root=Tk()
root.minsize(650,650)
root.maxsize(650,650)
root.configure(background="gray76")

open_image=ImageTk.PhotoImage(Image.open("open.png"))
save_image=ImageTk.PhotoImage(Image.open("save.png"))
play_image=ImageTk.PhotoImage(Image.open("pl.png"))


label1=Label(root,text="File name")
label1.place(relx=0.28,rely=0.03)

text_box=Entry(root)
text_box.place(relx=0.40,rely=0.03)

text_area=Text(root,height=35, width=79)
text_area.place(relx=0.005,rely=0.09)

file=("")
def remote():
    global file
    text_area.delete(1.0,END)
    text_box.delete(0,END)
    filename=filedialog.askopenfilename(title="open the file",filetypes=(("text files","*txt"),))
    print(filename)
    name=os.path.basename(filename)
    print(name)
    name1=name.split('.')[0]
    text_box.insert(END,name1)
    root.title(name1)
    filename=open(name,'r')
    para=filename.read()
    text_area.insert(END,para)
    filename.close()

open_btn=Button(root,image=open_image,text="open file",command=remote)
save_btn=Button(root,image=save_image,text="save")
play_btn=Button(root,image=play_image,text="play")

open_btn.place(relx=0.05,rely=0.03)
save_btn.place(relx=0.10,rely=0.03)
play_btn.place(relx=0.15,rely=0.03)

root.mainloop()