#include "mainwindow.h"
#include <QApplication>
#include "QLabel"
#include "QGridLayout"

class QGridLabelMatrix
{
    public:
        QGridLabelMatrix(const QGridLayout *grid) :
        g(grid)
    {
        Q_ASSERT(grid != 0);
    }

    QLabel* label(int row, int column) const
    {
        return qobject_cast<QLabel*>(g->itemAtPosition(row, column)->widget());
    }

    private:
        const QGridLayout *g;
};

int main(int argc, char *argv[])
{
    QImage peon_negro;
    peon_negro.load("/home/eduardo/Descargas/peonnegro.png");
    int rows = 3, columns = 3;
    QApplication a(argc, argv);
    //pensando para que sirve
    QGridLayout *grid = new QGridLayout();

    for(int i = 0; i < rows; i++) {
        for(int j = 0; j < columns; j++) {
            QLabel *label = new QLabel(QString("label %1").arg(i * columns + j + 1));

            grid->addWidget(label, i, j);
        }
    }

    // grid:
    // label1    label2    label3
    // label4    label5    label6
    // label7    label8    label9

    QGridLabelMatrix matrix(grid);
    matrix.label(0, 0)->setText("first");
    matrix.label(0, 2)->setText("right");
    matrix.label(2, 2)->setPixmap(QPixmap::fromImage(peon_negro));


    // now grid:
    // first     label2    right
    // label4    label5    label6
    // label7    label8    last

    QWidget w;
    w.setLayout(grid);
    //
    w.show();

    return a.exec();
}
