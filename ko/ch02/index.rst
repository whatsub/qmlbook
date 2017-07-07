========
시작하기
========

.. sectionauthor:: `jryannel <https://github.com/jryannel>`_

.. issues:: ch02

.. |creatorrun| image:: assets/qtcreator-run.png

이번 장에서는 Qt5로 개발하는 과정을 소개할 예정입니다. Qt SDK를 어떻게 설치하고 *hello world* 와 같은 간단한 애플리케이션을 작성해보면서 Qt Creator IDE를 어떻게 사용하는지 보여드리겠습니다.

.. note::

    본 장의 소스 코드는 `assets 폴더 <../../assets>`_ 에서 다운로드할 수 있습니다.


Qt5 SDK 설치하기
================

.. issues:: ch02

Qt SDK는 데스크탑이나 임베디드 응용 프로그램을 개발하는데 필요한 도구를 포함합니다. 최신 버전은 `Qt-Company <http://qt.io>`_ 홈페이지에서 확인할 수 있습니다. 오프라인 및 온라인 설치 프로그램이 있는데, 필자는 개인적으로 온라인 설치 프로그램을 선호합니다. 여러 Qt 버전을 설치하고 업데이트할 수 있기 때문입니다. 설치 프로그램을 이용하는 것이 Qt 개발을 시작하는데 권장되는 방법입니다. SDK 그 자체에는 SDK를 최신 버전으로 업데이트해주는 유지 관리 도구(MaintenanceTool)가 있습니다.

Qt SDK는 설치하기 쉬우며 *Qt Creator* 라는 자체 통합 개발 환경(IDE)이 함께 제공됩니다. 이 IDE는 Qt 코딩을 위해 개발된 매우 생산적인 환경이며 모든 독자에게 권장됩니다. 커맨드 라인에서 Qt를 사용하고 있는 개발자들도 많이 있기 때문에 여러분이 선호하는 코드 편집기를 자유롭게 사용할 수도 있습니다.

SDK를 설치할 때 기본 옵션을 선택하고 Qt 5.x이 활성화되어 있는지 확인하세요. 이제 다음 단계로 나갈 준비가 되었습니다.

Hello World
===========

.. issues:: ch02

설치가 잘 되었는지 확인하기 위해 작은 *hello world* 응용 프로그램을 만들어 보겠습니다. Qt Creator를 열고 Qt Quick UI 프로젝트를 생성해주세요. ( :menuselection:`File --> New File or Project --> Qt Quick Project --> Qt Quick UI` ) 그리고 프로젝트 이름은 ``HelloWorld`` 로 지정하세요.

.. note::

    Qt Creator IDE에서 다양한 유형의 응용 프로그램을 생성할 수 있습니다. 따로 명시하지 않으면 :guilabeL:`Qt Quick UI` 프로젝트를 생성하는 것으로 간주하세요.

.. hint::

    일반적인 Qt Quick 응용 프로그램은 초기 QML 코드를 로드하는 QmlEngine이라는 런타임을 통해 구동됩니다. 개발자는 이 런타임에 C++ 타입을 등록해서 네이티브 코드와 상호 작용할 수 있습니다. 이러한 C++ 타입은 플러그인 형태로 배포될 수 있으며 이 때는 import 구문을 통해 동적으로 로드됩니다. ``qmlscene`` 과 ``qml`` 도구는 QML 파일을 바로 테스트할 수 있도록 미리 만들어 놓은 런타임입니다. 여기에서는 네이티브쪽 개발보다는 Qt5의 QML에만 초점을 맞출 예정입니다.

프로젝트를 확인해보시면 Qt Creator가 여러 파일을 생성했을 것입니다. ``HelloWorld.qmlproject`` 파일은 프로젝트의 설정을 담고 있는 프로젝트 파일입니다. 이 파일은 Qt Creator가 관리하는 파일이기 때문에 수정하시는 마세요.

또 다른 파일인 ``HelloWorld.qml`` 는 우리의 응용 프로그램 코드입니다. 파일을 열어서 애플리케이션이 어떤 동작을 할 지 예상해보세요. 그 다음 이어지는 내용을 읽어주세요.

.. code-block:: js

    // HelloWorld.qml

    import QtQuick 2.5

    Rectangle {
        width: 360
        height: 360
        Text {
            anchors.centerIn: parent
            text: "Hello World"
        }
        MouseArea {
            anchors.fill: parent
            onClicked: {
                Qt.quit();
            }
        }
    }

``HelloWord.qml`` 은 QML 언어로 작성되었습니다. QML 언어는 다음 장에서 자세히 다룰 예정입니다. QML은 사용자 인터페이스의 구성 요소를 하나의 트리 형태로 기술합니다. 이 예제의 경우에 360 x 360 픽셀 크기의 사각형이 있고 그 가운데 "Hello World" 문구가 위치합니다. 사용자의 마우스 입력을 받기 위해 마우스 영역을 사각형의 크기만큼 확장했고, 사용자가 그 영역을 클릭하면 응용 프로그램은 종료합니다.

직접 응용 프로그램을 실행해보세요. 왼편에 |creatorrun| :guilabel:`Run` 도구 버튼을 누르거나 메뉴에서 :menuselection:`Build --> Run` 를 선택하시면 됩니다.

Qt Creator는 ``qmlscene`` 을 실행하고 첫번째 실행 인자로 QML 문서를 전달할 것입니다. ``qmlscene`` 은 문서를 파싱하고 기술된 UI를 실행할 것입니다. 이제 여러분은 아래와 같은 화면을 볼 수 있을 겁니다.

.. figure:: assets/example.png
    :scale: 50%

Qt5가 잘 동작하는 것 같고 다음 내용으로 이어갈 준비가 되었습니다.

.. tip::

    여러분이 시스템 통합 업무(system integrator)를 담당하고 있다면, 여러분이 개발하는 타겟 기기에 올릴 Qt 버전과 마찬가지로 안정된 최신 버전의 Qt SDK가 설치되길 원할 것입니다.

.. topic:: Build from Scratch

    만약 Qt5를 커맨드 라인 상에서 빌드하고 싶다면, 먼저 코드 저장소(code repository)의 복사본을 받아놓을 필요가 있습니다. 그리고 아래와 같이 빌드하세요.

    .. code-block:: sh

        git clone git://gitorious.org/qt/qt5.git
        cd qt5
        ./init-repository
        ./configure -prefix $PWD/qtbase -opensource
        make -j4


    커피를 2잔 정도 마시며 컴파일이 성공적으로 끝나길 기다리면, ``qtbase`` 폴더에 사용 가능한 Qt5가 만들어져 있을 것입니다. 어떤 음료라도 괜찮지만 최상의 결과를 위해 커피를 추천합니다.

    여러분의 컴파일 결과를 확인하고자 한다면, 간단히 ``qtbase/bin/qmlscene`` 을 실행하고 Qt Quick 예제 파일 중 하나를 선택해 실행해보세요. 아니면 다음 장까지 그냥 따라오셔도 무방합니다.


    설치가 잘 되었는지 확인하기 위해 작은 hello world 애플리케이션을 만들어 보겠습니다. 여러분이 선호하는 문서 편집기를 이용해 ``example.qml`` 파일을 생성하고 아래 내용을 붙여 넣으세요.

    .. code-block:: js

        // HelloWorld.qml

        import QtQuick 2.5

        Rectangle {
            width: 360
            height: 360
            Text {
                anchors.centerIn: parent
                text: "Greetings from Qt 5"
            }
            MouseArea {
                anchors.fill: parent
                onClicked: {
                    Qt.quit();
                }
            }
        }

    여러분은 이제 Qt5와 함께 딸려온 기본 런타임을 이용해 예제를 실행할 수 있게 되었습니다.

        $ qtbase/bin/qmlscene

애플리케이션 유형
=================

.. issues:: ch02

이번 장은 Qt5로 작성할 수 있는 여러가지 애플리케이션 유형에 대해 살펴보겠습니다. 이번 내용은 어떤 유형을 선택할 수 있는지 보여주는 것 뿐만 아니라, 일반적으로 Qt5를 이용해 무엇을 할 수 있는지 독자 여러분께 보여 드리고 더욱 잘 활용할 수 있도록 하는데 그 목적이 있습니다.

콘솔 애플리케이션
-----------------

.. issues:: ch02

콘솔 애플리케이션은 어떤 GUI도 제공하지 않습니다. 그리고 일반적으로 시스템 서비스의 일부로 호출되거나 커맨드 라인에서 실행됩니다. Qt5는 여러 플랫폼에서 실행 가능한 콘솔 애플리케이션을 개발하는데 도움을 주는 일련의 준비된(ready-made) 컴포넌트를 제공합니다. 예를 들어 네트워크 파일 API가 바로 그런 것입니다. 문자열 다루기, 그리고 5.1부터 추가된 효율적인 커맨드 라인 파서. Qt는 C++ 기반의 상위 레벨(high-level) API이기 때문에 실행 속도와 함께 개발 속도도 높여줍니다. Qt를 *단지* UI 툴킷으로만 생각하지 말아주세요. Qt는 훨씬 더 많은 것들을 제공합니다.

.. rubric:: 문자열 다루기

첫번째 예제는 두 개의 문자열 상수를 아주 간단하게 병합하는 것을 보여줍니다. 이것 자체로 매우 유용한 애플리케이션은 아니겠지만, 이벤트 루프(event loop)가 없는 네이티브 C++ 애플리케이션이 어떤 형상을 가지고 있는지 보여줍니다.


.. code-block:: cpp

    // module or class includes
    #include <QtCore>

    // text stream is text-codec aware
    QTextStream cout(stdout, QIODevice::WriteOnly);

    int main(int argc, char** argv)
    {
        // avoid compiler warnings
        Q_UNUSED(argc)
        Q_UNUSED(argv)
        QString s1("Paris");
        QString s2("London");
        // string concatenation
        QString s = s1 + " " + s2 + "!";
        cout << s << endl;
    }

.. rubric:: 컨테이너 클래스 (container classes)

이번 예제에서는 애플리케이션에 리스트와 리스트 반복자(list iterator)를 추가합니다. Qt는 사용하지 쉽고 다른 Qt 클래스와 같은 API 패러다임을 가진 많은 컨테이너 클래스들을 제공합니다.

.. code-block:: cpp

    QString s1("Hello");
    QString s2("Qt");
    QList<QString> list;
    // stream into containers
    list <<  s1 << s2;
    // Java and STL like iterators
    QListIterator<QString> iter(list);
    while(iter.hasNext()) {
        cout << iter.next();
        if(iter.hasNext()) {
            cout << " ";
        }
    }
    cout << "!" << endl;

여기에서는 문자열 리스트를 하나의 문자열로 결합해주는 좀더 발전된 리스트 함수를 보여줍니다. 이것은 라인 기반 텍스트 입력을 처리해야 할 때 매우 편리합니다. ``QString::split()`` 함수를 통해 반대 동작(문자열을 문자열 리스트로)도 물론 가능합니다.

.. code-block:: cpp


    QString s1("Hello");
    QString s2("Qt");
    // convenient container classes
    QStringList list;
    list <<  s1 << s2;
    // join strings
    QString s = list.join(" ") + "!";
    cout << s << endl;


.. rubric:: 파일 IO

다음 예제에서는 로컬 디렉토리에서 CSV 파일을 읽고 각각의 행을 돌면서 열을 추출해보겠습니다. 이렇게 하면 대략 20줄의 코드로 CSV 파일에서 테이블 데이터를 가져올 수 있습니다. 파일 읽기를 위해 바이트 스트림 (byte stream)를 제공하며 유효한 유니코드 텍스트(unicode text)로 변환해야 한다면 텍스트 스트림을 사용하고 저수준의 스트림(lower-level stream)으로 파일을 전달할 수도 있습니다. CSV 파일을 기록하려면 파일을 쓰기 모드로 열고 각 행을 텍스트 스트림과 연결(pipe)하기만 하면 됩니다.

.. code-block:: cpp


    QList<QStringList> data;
    // file operations
    QFile file("sample.csv");
    if(file.open(QIODevice::ReadOnly)) {
        QTextStream stream(&file);
        // loop forever macro
        forever {
            QString line = stream.readLine();
            // test for null string 'String()'
            if(line.isNull()) {
                break;
            }
            // test for empty string 'QString("")'
            if(line.isEmpty()) {
                continue;
            }
            QStringList row;
            // for each loop to iterate over containers
            foreach(const QString& cell, line.split(",")) {
                row.append(cell.trimmed());
            }
            data.append(row);
        }
    }
    // No cleanup necessary.

이번 파트에서 완성한 콘솔 기반 Qt 애플리케이션입니다.

위젯 애플리케이션
-----------------

.. issues:: ch02

콘솔 기반 애플리케이션은 매우 유용하지만 때로는 UI를 보여줄 필요가 있습니다. 또한 UI 기반 애플리케이션은 파일을 읽고 쓰거나 네트워크를 통해 통신하거나 컨테이너에 데이터를 보관하기 위한 백엔드를 필요로 할 것입니다.


위젯 기반 애플리케이션을 위한 첫번째 코드에서는 윈도우를 하나 만들고 표시하는데 필요한 정도의 작업만을 수행합니다. Qt의 세계에서 부모가 없는 위젯은 윈도우입니다. Scoped pointer를 사용해서 scoped pointer가 scope을 벗어날 때 위젯이 삭제되도록 할 것입니다. 애플리케이션 객체는 Qt 런타임을 캡슐화하고 ``exec()`` 호출로 이벤트 루프를 시작합니다. 거기로부터 애플리케이션은 마우스나 키보드 혹은 네트워크나 파일 IO와 같은 다른 이벤트 공급자로부터 발생된 이벤트에 반응합니다. 애플리케이션은 이벤트 루프가 종료될 때에만 종료됩니다. 이것은 애플리케이션에서 ``quit()`` 을 호출하거나 윈도우를 닫음으로써 수행됩니다.

코드를 수행하면 240 x 120 픽셀의 윈도우를 볼 수 있을 것입니다. 그게 다입니다.

.. code-block:: cpp

    #include <QtGui>

    int main(int argc, char** argv)
    {
        QApplication app(argc, argv);
        QScopedPointer<QWidget> widget(new CustomWidget());
        widget->resize(240, 120);
        widget->show();
        return app.exec();
    }

.. rubric:: 커스텀 위젯

사용자 인터페이스를 개발할 때는 커스텀 위젯을 생성해야 합니다. 일반적으로 하나의 위젯은 페인팅 함수 호출로 채워진 하나의 윈도우 영역입니다. 거기에 더해서 위젯은 키보드 혹은 마우스 입력의 처리 방법과 외부 이벤트에 반응하는 방법에 대한 내부 정보를 가지고 있습니다. Qt에서는 이를 위해 `QWidget` 클래스를 상속받아야 하고 페인팅이나 이벤트 처리를 위해 몇몇 함수를 덮어써야 합니다.

.. code-block:: cpp

    #ifndef CUSTOMWIDGET_H
    #define CUSTOMWIDGET_H

    #include <QtWidgets>

    class CustomWidget : public QWidget
    {
        Q_OBJECT
    public:
        explicit CustomWidget(QWidget *parent = 0);
        void paintEvent(QPaintEvent *event);
        void mousePressEvent(QMouseEvent *event);
        void mouseMoveEvent(QMouseEvent *event);
    private:
        QPoint m_lastPos;
    };

    #endif // CUSTOMWIDGET_H


이번에는 위젯에 작은 테두리를 그리고 마지막 마우스 위치에 작은 사각형을 그려 보겠습니다. 이러한 구현은 낮은 수준의 커스텀 위젯에서는 매우 일반적인 것입니다. 마우스나 키보드 이벤트는 위젯의 내부 상태를 변경하고 새롭게 페인팅할 것을 요청합니다. 이 코드에 대해서 너무 깊이 들어가길 원치는 않지만 여러분도 알아두시면 좋은 내용입니다. Qt에는 미리 만들어 놓은 데스크탑용 위젯이 많이 포함되어 있기 때문에 아마도 여러분이 직접 커스텀 위젯을 구현할 일은 많지 않을 것입니다.

.. code-block:: cpp


    #include "customwidget.h"

    CustomWidget::CustomWidget(QWidget *parent) :
        QWidget(parent)
    {
    }

    void CustomWidget::paintEvent(QPaintEvent *)
    {
        QPainter painter(this);
        QRect r1 = rect().adjusted(10,10,-10,-10);
        painter.setPen(QColor("#33B5E5"));
        painter.drawRect(r1);

        QRect r2(QPoint(0,0),QSize(40,40));
        if(m_lastPos.isNull()) {
            r2.moveCenter(r1.center());
        } else {
            r2.moveCenter(m_lastPos);
        }
        painter.fillRect(r2, QColor("#FFBB33"));
    }

    void CustomWidget::mousePressEvent(QMouseEvent *event)
    {
        m_lastPos = event->pos();
        update();
    }

    void CustomWidget::mouseMoveEvent(QMouseEvent *event)
    {
        m_lastPos = event->pos();
        update();
    }

.. rubric:: 데스크탑 위젯

Qt 개발자들은 이 모든 작업을 수행해왔으며 여러 OS에서 해당 OS 고유의 형상을 가진 데스크탑 위젯 집합을 제공합니다. 그 다음 여러분이 할 일은 이러한 다른 위젯들을 하나의 위젯 컨테이너에 배치하고 더 큰 패널에 추가하는 것입니다. Qt에서 하나의 위젯은 다른 위젯들의 컨테이너가 될 수도 있습니다. 이것은 부모-자식 관계에 의해 이루어집니다. 즉, 버튼, 체크 박스, 라이오 버튼과 같은 위젯들을 만드는 것도 필요하지만 다른 위젯의 자식을 나열하고 배치도 해야 합니다.

아래는 위젯 컨테이너라 불리는 헤더 파일입니다.

.. code-block:: cpp

    class CustomWidget : public QWidget
    {
        Q_OBJECT
    public:
        explicit CustomWidget(QWidget *parent = 0);
    private slots:
        void itemClicked(QListWidgetItem* item);
        void updateItem();
    private:
        QListWidget *m_widget;
        QLineEdit *m_edit;
        QPushButton *m_button;
    };

아래 코드 구현에서는 레이아웃을 사용해 위젯을 좀 더 잘 정렬합니다. 레이아웃 매니저는 컨테이너 위젯의 크기가 변경되었을 때 정해진 크기 정책에 따라 위젯을 다시 레이아웃합니다. 이 예제에서 클래스는 하나의 리스트와 하나의 line edit, 그리고 도시 리스트를 수정할 수 있게 해주는 세로로 정렬된 버튼을 가집니다. 우리는 Qt의 ``signal`` 과 ``slots`` 을 사용해 sender와 receiver 오브젝트를 연결합니다.

.. code-block:: cpp

    CustomWidget::CustomWidget(QWidget *parent) :
        QWidget(parent)
    {
        QVBoxLayout *layout = new QVBoxLayout(this);
        m_widget = new QListWidget(this);
        layout->addWidget(m_widget);

        m_edit = new QLineEdit(this);
        layout->addWidget(m_edit);

        m_button = new QPushButton("Quit", this);
        layout->addWidget(m_button);
        setLayout(layout);

        QStringList cities;
        cities << "Paris" << "London" << "Munich";
        foreach(const QString& city, cities) {
            m_widget->addItem(city);
        }

        connect(m_widget, SIGNAL(itemClicked(QListWidgetItem*)), this, SLOT(itemClicked(QListWidgetItem*)));
        connect(m_edit, SIGNAL(editingFinished()), this, SLOT(updateItem()));
        connect(m_button, SIGNAL(clicked()), qApp, SLOT(quit()));
    }

    void CustomWidget::itemClicked(QListWidgetItem *item)
    {
        Q_ASSERT(item);
        m_edit->setText(item->text());
    }

    void CustomWidget::updateItem()
    {
        QListWidgetItem* item = m_widget->currentItem();
        if(item) {
            item->setText(m_edit->text());
        }
    }

.. rubric:: 모양 그리기

어떤 문제는 체계적인 시각화를 요구하기도 합니다. 만약 기하학적인 객체처럼 손에 바로 잡히지 않는 문제라면, Qt graphics view가 좋은 해법입니다. Graphics view는 하나의 scene 위에 간단한 기하학적인 모양을 정렬합니다. 사용자는 이러한 모양들과 상호작용하거나 어떤 알고리즘에 따라 배치할 수도 있습니다. 하나의 graphics view를 추가하려면 graphics view와 graphics scene이 필요합니다. 이 때 scene이 view에 첨부되어(attached) graphics item으로 추가됩니다.
다음은 간단한 예제입니다. 먼저 view와 scene의 선언이 있는 헤더 파일입니다.

.. code-block:: cpp

    class CustomWidgetV2 : public QWidget
    {
        Q_OBJECT
    public:
        explicit CustomWidgetV2(QWidget *parent = 0);
    private:
        QGraphicsView *m_view;
        QGraphicsScene *m_scene;

    };

구현부에서 scene은 먼저 view에 첨부됩니다(attached). 이 때 view는 하나의 위젯이고 컨테이너 위젯 안에 정렬됩니다. 마지막으로 scene에 작은 직사각형을 추가합니다. 이 사각형은 view 위에서 렌더링될 것입니다.

.. code-block:: cpp

    #include "customwidgetv2.h"

    CustomWidget::CustomWidget(QWidget *parent) :
        QWidget(parent)
    {
        m_view = new QGraphicsView(this);
        m_scene = new QGraphicsScene(this);
        m_view->setScene(m_scene);

        QVBoxLayout *layout = new QVBoxLayout(this);
        layout->setMargin(0);
        layout->addWidget(m_view);
        setLayout(layout);

        QGraphicsItem* rect1 = m_scene->addRect(0,0, 40, 40, Qt::NoPen, QColor("#FFBB33"));
        rect1->setFlags(QGraphicsItem::ItemIsFocusable|QGraphicsItem::ItemIsMovable);
    }

데이터 가져오기
---------------

.. issues:: ch02


지금까지 우리는 대부분 기본 데이터 타입과 위젯 및 graphics view의 사용 방법에 대해 다뤘습니다. 애플리케이션을 개발하다보면 종종 대량의 구조화된 데이터를 필요로 할 때가 있고 어떤 데이터를 영구히 저장해야 할 경우도 있습니다. 그리고 화면에 표시해야 할 데이터도 있습니다. 이를 위해 Qt는 모델을 사용합니다. 여기에 간단한 모델의 예가 있습니다. 문자열로 채워진 문자열 리스트 모델(string list model)은 리스트뷰(list view)에 첨부됩니다.

.. code-block:: cpp

    m_view = new QListView(this);
    m_model = new QStringListModel(this);
    view->setModel(m_model);

    QList<QString> cities;
    cities << "Munich" << "Paris" << "London";
    model->setStringList(cities);

데이터를 저장하거나 가져오는 보다 체계적인 방법은 SQL입니다. Qt에는 SQLite가 내장되어 있고 다른 데이터베이스 엔진(MySQL, PostgresSQL, ...)도 지원합니다. 먼저 다음과 같은 schema를 사용하여 데이터베이스를 작성해봅시다.

.. code-block:: sql

    CREATE TABLE city (name TEXT, country TEXT);
    INSERT INTO city value ("Munich", "Germany");
    INSERT INTO city value ("Paris", "France");
    INSERT INTO city value ("London", "United Kingdom");

SQL을 사용하기 위해서 여러분의 .pro 파일에 SQL 모듈을 추가해야 합니다.

.. code-block:: cpp

    QT += sql

그런 다음 C++ 코드를 통해 데이터베이스를 열 수 있습니다. 먼저 지정된 데이터베이스 엔진을 위한 새로운 데이터베이스 객체를 가져와야 합니다. 이 데이터베이스 객체를 가지고 데이터베이스를 엽니다. SQLite의 경우에는 데이터베이스 파일에 대한 경로를 지정하는 것으로 충분합니다. Qt는 일부 고수준(high-level)의 데이터베이스 모델을 제공합니다. 그중 하나가 테이블 식별자와 데이터를 선택할 수 있는 where 절을 추가할 수 있는 테이블 모델입니다. 그 결과로 생성된 모델은 앞선 다른 모델처럼 list view에 첨부될 수 있습니다.

.. code-block:: cpp

    QSqlDatabase db = QSqlDatabase::addDatabase("QSQLITE");
    db.setDatabaseName('cities.db');
    if(!db.open()) {
        qFatal("unable to open database");
    }

    m_model = QSqlTableModel(this);
    m_model->setTable("city");
    m_model->setHeaderData(0, Qt::Horizontal, "City");
    m_model->setHeaderData(1, Qt::Horizontal, "Country");

    view->setModel(m_model);
    m_model->select();

더 높은 수준의 모델 작업을 위해 Qt에서는 정렬 파일 프록시 모델(sort file proxy model)을 제공합니다. 이 모델은 다른 모델을 정렬하고 필터링할 수 있게 하는 기본적인 구조를 제공합니다.

.. code-block:: cpp

    QSortFilterProxyModel* proxy = new QSortFilterProxyModel(this);
    proxy->setSourceModel(m_model);
    view->setModel(proxy);
    view->setSortingEnabled(true);

필터링은 필터될 열과 필터 조건인 문자열을 바탕으로 수행됩니다.

.. code-block:: cpp

    proxy->setFilterKeyColumn(0);
    proxy->setFilterCaseSensitive(Qt::CaseInsensitive);
    proxy->setFilterFixedString(QString)

필터 프록시 모델(filter proxy model)은 여기서 설명한 것보다 훨씬 강력합니다. 지금은 그 존재만 기억하는 것으로 충분합니다.


.. note::

    여기까지 Qt5로 개발할 수 있는 다양한 종류의 고전적인(classical) 애플리케이션에 대한 개요였습니다. 데스크탑 시장은 변하고 있으며 곧 모바일 기기가 내일의 데스크탑이 될 것입니다. 모바일 장치의 사용자 인터페이스 디자인은 데스크탑과 달리 훨씬 단순합니다. 한가지 목적된 기능에 집중하고 그것을 직관적인 방식으로 제공합니다. 애니메이션은 사용자 경험에서 중요한 부분입니다. 사용자 인터페이스는 생동감 있고 유려해야 합니다. 전통적인 Qt의 기술은 이러한 시장에 적합하지 않습니다.

    다음 이야기: 난세 영웅 Qt Quick (Qt Quick for the rescue).

Qt Quick 애플리케이션
---------------------

.. issues:: ch02

현대 소프트웨어 개발에는 내재적인 갈등이 존재합니다. 사용자 인터페이스는 백엔드 서비스보다 훨씬 빠르게 변하고 있습니다. 전통적인 기술에서는 소위 말하는 프론트 엔드를 백엔드와 같은 속도감으로 개발해왔습니다. 이런 방식에서는 고객이 프로젝트 중 사용자 인터페이스를 변경하거나 프로젝트를 진행하면서 사용자 인터페이스를 발전시켜 나가려고 할 때 충돌이 발생합니다. 기민한 프로젝트(agile project)에는 기민한 방법론(agile methods: 애자일 방법론)이 필요합니다.

Qt Quick은 사용자 인터페이스(프론트 엔드)가 HTML처럼 선언되고 백엔드는 네이티브 C++코드로 구현되는 선언적인 환경을 제공합니다. 이러한 개발 방식은 두 세계의 장점을 취할 수 있게 해줍니다.

아래에 간단한 Qt Quick UI가 있습니다.

.. code-block:: qml

    import QtQuick 2.5

    Rectangle {
        width: 240; height: 1230
        Rectangle {
            width: 40; height: 40
            anchors.centerIn: parent
            color: '#FFBB33'
        }
    }

이 선언적 언어는 QML이라 불리며, 실행을 위해서는 런타임이 필요합니다. Qt는 ``qmlscene`` 이라고 하는 표준 런타임을 제공하지만 커스텀 런타임을 작성하는 것도 그리 어렵지 않습니다. Quick view에 main QML 문서를 소스로 설정하는 것만으로도 충분합니다. 그 다음 사용자 인터페이스를 보여주면 끝입니다.

.. code-block:: cpp

    QQuickView* view = new QQuickView();
    QUrl source = QUrl::fromLocalFile("main.qml");
    view->setSource(source);
    view.show();

이전 예제로 돌아가봅시다. 그 중 한 예제에서 우리는 C++로 작성한 도시의 모델을 사용했습니다. 선언적인 QML 코드에서도 이 모델을 사용할 수 있다면 좋겠죠.

이를 가능하게 하기 위해, 프론트 엔드를 먼저 코딩해서 도시 모델을 어떻게 사용할 지 확인하겠습니다. 이 경우에 프론트 엔드는 ``cityModel`` 라는 이름의 객체가 도시 모델을 담을 것이라 예상하고 그것을 list view 내에서 사용하겠습니다.

.. code-block:: qml

    import QtQuick 2.5

    Rectangle {
        width: 240; height: 120
        ListView {
            width: 180; height: 120
            anchors.centerIn: parent
            model: cityModel
            delegate: Text { text: model.city }
        }
    }

``cityModel`` 이 동작하도록 하기 위해 앞서 만들었던 모델을 재사용하고, root context(root context는 main 문서의 root element입니다)에 context property로 추가합니다. 

.. code-block:: cpp

    m_model = QSqlTableModel(this);
    ... // some magic code
    QHash<int, QByteArray> roles;
    roles[Qt::UserRole+1] = "city";
    roles[Qt::UserRole+2] = "country";
    m_model->setRoleNames(roles);
    view->rootContext()->setContextProperty("cityModel", m_model);

.. hint::

    이것으로 완전하게 구현된 것은 아닙니다. SQL 테이블 모델은 데이터가 열(column)에 포함되어 있고, QML 모델은 데이터가 역할(role)로 명시되어 있길 기대하기 때문입니다. 그래서 열과 역할 간 매핑이 필요합니다. 자세한 내용은 `QML and QSqlTableModel <http://wiki.qt.io/QML_and_QSqlTableModel>`_ 위키 문서를 참조해주세요.


요약
====

.. issues:: ch02

우리는 Qt SDK의 설치 방법과 첫번째 애플리케이션을 어떻게 만드는지 살펴 보았습니다. 그 다음 Qt에 대한 개괄적인 이해를 돕기 위해 다양한 애플리케이션 유형을 경험해보았고, 애플리케이션 개발을 위해 Qt가 제공하는 몇 가지 기능을 살펴보았습니다. Qt는 매우 풍부한 UI 툴킷이고 애플리케이션 개발자가 바라는 그 이상의 것까지도 제공한다는 좋은 느낌을 받으셨길 바랍니다. 과거에도 그랬지만 지금까지도, Qt는 여러분을 특정 라이브러리에 종속시키지 않습니다. 여러분은 언제든 다른 라이브러리를 사용할 수 있고 직접 Qt를 확장하면서 사용할 수 있기 때문입니다. 그리고 콘솔, 테스크탑 UI, 터치 기반 사용자 인터페이스와 같은 다양한 애플리케이션 모델을 지원할 때도 유용합니다.



