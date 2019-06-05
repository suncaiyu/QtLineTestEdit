# QtLineTestEdit
两个可以显示行号的QTextEdit
#include "mainwindow.h"
#include "ui_mainwindow.h"
#include <QtDebug>

MainWindow::MainWindow(QWidget *parent) :
    QMainWindow(parent),
    ui(new Ui::MainWindow)
{
    ui->setupUi(this);
    setAutoFillBackground(true);//必须有这条语句
    setPalette(QPalette(QColor(250,250,200)));
    ui->lineEdit->setStyleSheet("background-color:rgb(40,190,66)");
    ui->pushButton->setStyleSheet("background-color:green");
    ui->pushButton_2->setStyleSheet("background-color:rgb(100,120,120)");
    setWindowFlags(Qt::FramelessWindowHint);
    setWindowOpacity(0.8);
}

MainWindow::~MainWindow()
{
    delete ui;
}

void MainWindow::mousePressEvent(QMouseEvent* e)

{
         if(e->button() ==  Qt::LeftButton)
         {
                   m_bIsWindowMoveable = true;
         }

}

void MainWindow::mouseMoveEvent(QMouseEvent*e)

{
         if(m_bIsWindowMoveable)
         {
                   move(e->globalPos());
         }

}

void MainWindow::mouseReleaseEvent(QMouseEvent* e)
{
         m_bIsWindowMoveable = false;
}
