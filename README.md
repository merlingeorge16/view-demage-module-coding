

from PyQt5 import QtCore, QtGui, QtWidgets
from PyQt5.QtWidgets import QMessageBox
from PyQt5.QtCore import *
import sqlite3

class Ui_Dialogm5(object):
    def submit(self):
        db = sqlite3.connect('asset.db')
        c = db.cursor()
        emp_id = self.t_amac1.text()
        emp_name = self.t_amac2.text()
        emp_type = self.t_amac3.text()
        emp_addr = self.t_amac4.text()
        emp_ph = self.t_amac5.text()

        

        try :
                c.execute('INSERT INTO damage_details (name,model,type,dept,descn)VALUES(?,?,?,?,?)',(emp_id,emp_name,emp_type,emp_addr,emp_ph))
                db.commit()
                msg = QMessageBox()
                msg.setText("Damage Details Added!");
                msg.exec_()
                
        except :
                db.rollback()
                msg = QMessageBox()
                msg.setText("Not Saved!");
                msg.exec_()
        
        c.close()
    def setupUi(self, Dialog):
        Dialog.setObjectName("Dialog")
        Dialog.resize(1000, 600)
        self.label = QtWidgets.QLabel(Dialog)
        self.label.setGeometry(QtCore.QRect(300, 40, 431, 61))
        font = QtGui.QFont()
        font.setFamily("Modern No. 20")
        font.setPointSize(27)
        font.setBold(False)
        font.setWeight(50)
        self.label.setFont(font)
        self.label.setObjectName("label")
        self.t_amac1 = QtWidgets.QLineEdit(Dialog)
        self.t_amac1.setGeometry(QtCore.QRect(460, 120, 201, 31))
        self.t_amac1.setObjectName("t_amac1")
        self.label_2 = QtWidgets.QLabel(Dialog)
        self.label_2.setGeometry(QtCore.QRect(310, 120, 111, 31))
        font = QtGui.QFont()
        font.setPointSize(11)
        self.label_2.setFont(font)
        self.label_2.setObjectName("label_2")
        self.t_amac2 = QtWidgets.QLineEdit(Dialog)
        self.t_amac2.setGeometry(QtCore.QRect(460, 180, 201, 31))
        self.t_amac2.setObjectName("t_amac2")
        self.label_3 = QtWidgets.QLabel(Dialog)
        self.label_3.setGeometry(QtCore.QRect(310, 180, 111, 31))
        font = QtGui.QFont()
        font.setPointSize(11)
        self.label_3.setFont(font)
        self.label_3.setObjectName("label_3")
        self.t_amac3 = QtWidgets.QLineEdit(Dialog)
        self.t_amac3.setGeometry(QtCore.QRect(460, 240, 201, 31))
        self.t_amac3.setObjectName("t_amac3")
        self.t_amac4 = QtWidgets.QLineEdit(Dialog)
        self.t_amac4.setGeometry(QtCore.QRect(460, 300, 201, 31))
        self.t_amac4.setObjectName("t_amac4")
        self.t_amac5 = QtWidgets.QLineEdit(Dialog)
        self.t_amac5.setGeometry(QtCore.QRect(460, 360, 201, 31))
        self.t_amac5.setObjectName("t_amac5")
        self.label_8 = QtWidgets.QLabel(Dialog)
        self.label_8.setGeometry(QtCore.QRect(310, 240, 111, 31))
        font = QtGui.QFont()
        font.setPointSize(11)
        self.label_8.setFont(font)
        self.label_8.setObjectName("label_8")
        self.label_9 = QtWidgets.QLabel(Dialog)
        self.label_9.setGeometry(QtCore.QRect(310, 300, 111, 31))
        font = QtGui.QFont()
        font.setPointSize(11)
        self.label_9.setFont(font)
        self.label_9.setObjectName("label_9")
        self.btn_submit = QtWidgets.QPushButton(Dialog)
        self.btn_submit.setGeometry(QtCore.QRect(460, 420, 91, 31))
        font = QtGui.QFont()
        font.setPointSize(12)
        self.btn_submit.setFont(font)
        self.btn_submit.setObjectName("btn_submit")
        self.btn_submit.clicked.connect(self.submit)
        self.label_10 = QtWidgets.QLabel(Dialog)
        self.label_10.setGeometry(QtCore.QRect(310, 360, 111, 31))
        font = QtGui.QFont()
        font.setPointSize(11)
        self.label_10.setFont(font)
        self.label_10.setObjectName("label_10")

        self.retranslateUi(Dialog)
        QtCore.QMetaObject.connectSlotsByName(Dialog)

    def retranslateUi(self, Dialog):
        _translate = QtCore.QCoreApplication.translate
        Dialog.setWindowTitle(_translate("Dialog", "Dialog"))
        self.label.setText(_translate("Dialog", "Damaged Machinery Details"))
        self.label_2.setText(_translate("Dialog", "Machine Name"))
        self.label_3.setText(_translate("Dialog", "Model"))
        self.label_8.setText(_translate("Dialog", "Type"))
        self.label_9.setText(_translate("Dialog", "Department"))
        self.btn_submit.setText(_translate("Dialog", "Submit"))
        self.label_10.setText(_translate("Dialog", "Damage Desc."))


if __name__ == "__main__":
    import sys
    app = QtWidgets.QApplication(sys.argv)
    Dialog = QtWidgets.QDialog()
    ui = Ui_Dialogm5()
    ui.setupUi(Dialog)
    Dialog.show()
    sys.exit(app.exec_())

