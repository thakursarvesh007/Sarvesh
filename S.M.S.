from tkinter import *
from tkinter.messagebox import *
from tkinter.scrolledtext import *
from sqlite3 import *

def main_to_add():
	root_mw.withdraw()
	root_adw.deiconify()
	adw_ent_rn.focus()

def add_to_main():
	root_adw.withdraw()
	root_mw.deiconify()
	
def main_to_view():
	root_mw.withdraw()
	root_vw.deiconify()
	vw_st_data.delete(1.0,END)
	view()

def view_to_main():
	root_vw.withdraw()
	root_mw.deiconify()

def main_to_upd():
	root_mw.withdraw()
	root_updw.deiconify()
	updw_ent_rn.focus()

def upd_to_main():
	root_updw.withdraw()
	root_mw.deiconify()

def main_to_del():
	root_mw.withdraw()
	root_del.deiconify()
	del_ent_rn.focus()

def del_to_main():
	root_del.withdraw()
	root_mw.deiconify()

def add():
	try:
		rn = adw_ent_rn.get()
		if rn =="":
			showerror("Roll no. issue","roll no cannot be empty")
			adw_ent_rn.focus()
			return
		elif float(rn) < 1:
			showerror("Roll no. issue","roll no should be greater than 1 always")
			adw_ent_rn.focus()
			return

		nm = adw_ent_nm.get()
		if nm == "":
			showerror("Name issue","name cannot be empty")
			adw_ent_nm.focus()
			return
				
		s1 = adw_s1_ent.get()
		s2 = adw_s2_ent.get()
		s3 = adw_s3_ent.get()

		if s1 == "":
			showerror("Subject 1 issue","Subject 1 cannot be empty ")
			adw_s1_ent.focus()
			return
		elif float(s1) < 0:
			showerror("Subject 1 issue","Subject 1 should be greater than 0 ")
			adw_s1_ent.focus()
			return
		if s2 == "":
			showerror("Subject 2 issue","Subject 2 cannot be empty ")
			adw_s2_ent.focus()
			return
		elif float(s2) < 0:
			showerror("Subject 2 issue","Subject 2 should be greater than 0 ")
			adw_s2_ent.focus()
			return
		if s3 == "":
			showerror("Subject 3 issue","Subject 3 cannot be empty ")
			adw_s3_ent.focus()
			return
		elif float(s3) < 0:
			showerror("Subject 3 issue","Subject 3 should be greater than 0 ")
			adw_s3_ent.focus()
			return	

		con = None
		con = connect("st.db")
		sql = "insert into sms1 values('%d','%s','%d','%d','%d')"
		cursor = con.cursor()
		cursor.execute(sql % (int(rn),nm,int(s1),int(s2),int(s3)))
		con.commit()
		showinfo("success","Details added successfully ")
		adw_ent_rn.delete(0,END)
		adw_ent_nm.delete(0,END)
		adw_s1_ent.delete(0,END)
		adw_s2_ent.delete(0,END)
		adw_s3_ent.delete(0,END)
		adw_ent_rn.focus()

	except Exception as e:
		con.rollback()
		showerror("issue",e)
	finally:
		if con is not None:
			con.close()

def view():
	con = None		
	try:
		con = connect("st.db")
		sql = "select * from sms1"
		cursor = con.cursor()
		cursor.execute(sql)
		data = cursor.fetchall()
		info = ""
		info1 = ""
		for d in data:
			info1 = "Roll No" +"\t\t" + "Name" +"\t\t"+ "Sub1"+"\t"+ "Sub2"+"\t"+ "Sub3"+ "\n" + "-----------------------------------------------------------------------------------------"
			info = info  +"\n"+"    " +str(d[0])  +"\t\t " + str(d[1])  +"\t\t" +"  "+ str(d[2]) +"\t" +"  "+ str(d[3]) +"\t" +"  "+ str(d[4])
		vw_st_data.insert(INSERT,info1)
		vw_st_data.insert(INSERT,info)

	except Exception as e:
		con.rollback()
		showerror("issue",e)
	finally:
		if con is not None:
			con.close()

def update():
	try:
		rn = updw_ent_rn.get()
		if rn =="":
			showerror("Roll no. issue","roll no cannot be empty")
			updw_ent_rn.focus()
			return
		elif float(rn) < 1:
			showerror("Roll no. issue","roll no should be greater than 1 always")
			updw_ent_rn.focus()
			return

		nm = updw_ent_nm.get()
		if nm == "":
			showerror("Name issue","name cannot be empty")
			updw_ent_nm.focus()
			return
				
		s1 = updw_s1_ent.get()
		s2 = updw_s2_ent.get()
		s3 = updw_s3_ent.get()

		if s1 == "":
			showerror("Subject 1 issue","Subject 1 cannot be empty ")
			updw_s1_ent.focus()
			return
		elif float(s1) < 0:
			showerror("Subject 1 issue","Subject 1 should be greater than 0 ")
			updw_s1_ent.focus()
			return
		if s2 == "":
			showerror("Subject 2 issue","Subject 2 cannot be empty ")
			updw_s2_ent.focus()
			return
		elif float(s2) < 0:
			showerror("Subject 2 issue","Subject 2 should be greater than 0 ")
			updw_s2_ent.focus()
			return
		if s3 == "":

			showerror("Subject 3 issue","Subject 3 cannot be empty ")
			updw_s3_ent.focus()
			return
		elif float(s3) < 0:
			showerror("Subject 3 issue","Subject 3 should be greater than 0 ")
			updw_s3_ent.focus()
			return

		con = None

		con = connect("st.db")
		sql = "update sms1 set nm ='%s',s1 = '%d',s2 = '%d',s3 ='%d' where rn = '%d'"
		cursor = con.cursor()
		cursor.execute(sql % (str(nm),int(s1),int(s2),int(s3),int(rn)))
		con.commit()
		data = cursor.fetchall()
		info = ""
		for d in data:
			info = info + "rno = " + str(d[4]) + " name = " + str(d[0]) + " subject 1 = " + str(d[1]) + " subject 2 = " + str(d[2]) + " subject 3 = " + str(d[3]) + "\n"
		vw_st_data.insert(INSERT,info)
		showinfo("success","Updated info")
		updw_ent_rn.delete(0,END)
		updw_ent_nm.delete(0,END)
		updw_s1_ent.delete(0,END)
		updw_s2_ent.delete(0,END)
		updw_s3_ent.delete(0,END)
		updw_ent_rn.focus()
	except Exception as e:
		con.rollback()
		showerror("issue",e)
	finally:
		if con is not None:
			con.close()

def delete():
	try:
		rn = del_ent_rn.get()
		if rn =="":
			showerror("Roll no. issue","roll no cannot be empty")
			del_ent_rn.focus()
			return
		elif float(rn) < 1:
			showerror("Roll no. issue","roll no should be greater than 1 always")
			del_ent_rn.focus()
			return

		con = None
		con = connect("st.db")
		sql = "delete from sms1 where rn = '%d'"
		cursor = con.cursor()
		cursor.execute(sql % int(rn))
		con.commit()
		vw_st_data.delete(float(rn),END)
		showinfo("success","Record Deleted")
		del_ent_rn.delete(0,END)
		del_ent_rn.focus()
	except Exception as e:
		con.rollback()
		showerror("issue",e)
	finally:
		if con is not None:
			con.close()

#Splash Window

sw = Tk()
sw.geometry("600x600+300+20")
sw.overrideredirect(True)
lab = Label(sw,text="App \nby \nSarvesh",font=("Cambria",80,"bold"),fg="blue")
lab.pack(pady=50)

def sw_to_mw():
	sw.destroy()

sw.after(2000,sw_to_mw)
sw.mainloop()		
		
# ------->>>>> MAIN WINDOW  <<<<<<---------

root_mw = Tk()
root_mw.title("S.M.S.")
root_mw.geometry("700x600+300+20")
f =("Arial",20,"bold")

root_mw.configure(bg="PaleGreen")

mw_Label = Label(root_mw,text="Main Screen",font=f,bg="PaleGreen")
mw_Label.pack(pady=20)

add_mw_btn = Button(root_mw,text="Add details",font=f,width=13,command=main_to_add)
add_mw_btn.pack(pady=10)

view_mw_btn = Button(root_mw,text="View  details",font=f,width=13,command=main_to_view)
view_mw_btn.pack(pady=10)

upt_mw_btn = Button(root_mw,text="Update  details",font=f,width=13,command=main_to_upd)
upt_mw_btn.pack(pady=10)

del_mw_btn = Button(root_mw,text="Delete  details",font=f,width=13,command=main_to_del)
del_mw_btn.pack(pady=10)

# ------->>>>> ADD WINDOW  <<<<<<---------

root_adw = Toplevel(root_mw)
root_adw.title("Add Student Info")
root_adw.geometry("600x700+300+20")

root_adw.configure(bg="medium aquamarine")

adw_rn_Label = Label(root_adw,text="Enter Roll No.",font=f,bg="medium aquamarine")
adw_rn_Label.pack(pady=5)

adw_ent_rn = Entry(root_adw,font=f)
adw_ent_rn.pack(pady=5)

adw_nm_Label = Label(root_adw,text="Enter Student's Name",font=f,bg="medium aquamarine")
adw_nm_Label.pack(pady=5)

adw_ent_nm = Entry(root_adw,font=f)
adw_ent_nm.pack(pady=5)

adw_s1_Label = Label(root_adw,text="Enter Subject 1 Marks",font=f,bg="medium aquamarine")
adw_s1_Label.pack(pady=5)

adw_s1_ent = Entry(root_adw,font=f)
adw_s1_ent.pack(pady=5)

adw_s2_Label = Label(root_adw,text="Enter Subject 2 Marks",font=f,bg="medium aquamarine")
adw_s2_Label.pack(pady=5)

adw_s2_ent = Entry(root_adw,font=f)
adw_s2_ent.pack(pady=5)

adw_s3_Label = Label(root_adw,text="Enter Subject 3 Marks",font=f,bg="medium aquamarine")
adw_s3_Label.pack(pady=5)

adw_s3_ent = Entry(root_adw,font=f)
adw_s3_ent.pack(pady=5)

adw_add_btn = Button(root_adw,text="Add details",font=f,width=13,command=add)
adw_add_btn.pack(pady=5)

adw_back_btn = Button(root_adw,text="Back to main",font=f,width=13,command=add_to_main)
adw_back_btn.pack(pady=5)

root_adw.withdraw()

# ------->>>>> VIEW WINDOW  <<<<<<---------

root_vw = Toplevel(root_mw)
root_vw.title("View Student Info")
root_vw.geometry("800x900+300+20")
f1 = ("Arial",15,"bold")

root_vw.configure(bg="pink3")

vw_st_data = ScrolledText(root_vw,font=f1,width=60,height=20)
vw_st_data.pack(pady=10)
vw_back_btn = Button(root_vw,text="Back to main",font=f1,width=13,command=view_to_main)
vw_back_btn.pack(pady=10)

root_vw.withdraw()

# ------->>>>> UPDATE WINDOW  <<<<<<---------

root_updw = Toplevel(root_mw)
root_updw.title("Update Student Info")
root_updw.geometry("600x700+300+20")

root_updw.configure(bg="aquamarine2")

updw_rn_Label = Label(root_updw,text="Enter Roll No.",font=f,bg="aquamarine2")
updw_rn_Label.pack(pady=5)

updw_ent_rn = Entry(root_updw,font=f)
updw_ent_rn.pack(pady=5)

updw_nm_Label = Label(root_updw,text="Enter Student's Name",font=f,bg="aquamarine2")
updw_nm_Label.pack(pady=5)

updw_ent_nm = Entry(root_updw,font=f)
updw_ent_nm.pack(pady=5)

updw_s1_Label = Label(root_updw,text="Enter Subject 1 Marks",font=f,bg="aquamarine2")
updw_s1_Label.pack(pady=5)

updw_s1_ent = Entry(root_updw,font=f)
updw_s1_ent.pack(pady=5)

updw_s2_Label = Label(root_updw,text="Enter Subject 2 Marks",font=f,bg="aquamarine2")
updw_s2_Label.pack(pady=5)

updw_s2_ent = Entry(root_updw,font=f)
updw_s2_ent.pack(pady=5)

updw_s3_Label = Label(root_updw,text="Enter Subject 3 Marks",font=f,bg="aquamarine2")
updw_s3_Label.pack(pady=5)

updw_s3_ent = Entry(root_updw,font=f)
updw_s3_ent.pack(pady=5)

updw_add_btn = Button(root_updw,text="Update details",font=f,width=13,command=update)
updw_add_btn.pack(pady=5)

updw_back_btn = Button(root_updw,text="Back to main",font=f,width=13,command=upd_to_main)
updw_back_btn.pack(pady=5)

root_updw.withdraw()

# ------->>>>> DELETE WINDOW  <<<<<<---------

root_del = Toplevel(root_mw)
root_del.title("Delete Student Info")
root_del.geometry("700x600+300+20")

root_del.configure(bg="aquamarine4")

del_rn_Label = Label(root_del,text="Enter Roll No.",font=f,bg="aquamarine4")
del_rn_Label.pack(pady=10)

del_ent_rn = Entry(root_del,font=f)
del_ent_rn.pack(pady=10)

del_save_btn = Button(root_del,text="Delete details",font=f,width=13,command=delete)
del_save_btn.pack(pady=10)

del_back_btn = Button(root_del,text="Back to main",font=f,width=13,command=del_to_main)
del_back_btn.pack(pady=10)

root_del.withdraw()

def on_closing():
	if askyesno("exit","do you want to exit "):
		root_mw.destroy()

root_mw.protocol("WM_DELETE_WINDOW",on_closing)
root_adw.protocol("WM_DELETE_WINDOW",on_closing)
root_vw.protocol("WM_DELETE_WINDOW",on_closing)
root_updw.protocol("WM_DELETE_WINDOW",on_closing)
root_del.protocol("WM_DELETE_WINDOW",on_closing)

root_mw.mainloop()
