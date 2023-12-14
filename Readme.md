
```
class MainWindow : public QMainWindow { 
  //...
};

void MainWindow::configGeometry()
{
  setWindowState(Qt::WindowFullScreen);

#ifdef DEBUG
  QScreen* screen;

  if (QGuiApplication::screens().size() > 1) {
    screen = QGuiApplication::screens().at(1);
  }
  else {
    screen = QGuiApplication::screens().at(0);
  }

  const QRect g = screen->geometry();
  const QPoint c = screen->geometry().center();
  setGeometry(0, 0, g.width(), g.height());
  move(c.x() - static_cast<int>(0.5 * width()), c.y() - static_cast<int>(0.5 * height()));
#endif
}

```

