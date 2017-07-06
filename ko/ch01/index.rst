=================
Qt5를 소개합니다.
=================

.. sectionauthor:: `jryannel <https://github.com/jryannel>`_

.. issues:: ch01

.. note::

    본 장의 소스 코드는 `assets 폴더 <../../assets>`_ 에서 다운로드할 수 있습니다.

이 책을 통해 여러분은 Qt 5.x 버전을 이용한 애플리케이션 개발의 다양한 측면을 하나씩 습득해 나갈 수 있습니다. 여기에서는 Qt Quick이라는 새로운 기술에 중점을 두면서, C++ 백엔드(back-ends)를 작성하고 Qt Quick의 기능을 확장하는데 필요한 정보도 함께 제공합니다.

본 장에서는 Qt5를 개괄적으로 소개할 예정입니다. Qt5에서 사용 가능한 여러가지 애플리케이션 모델과 신기능을 보여주는 쇼케이스 애플리케이션을 보여드릴 것입니다. 그리고 Qt5에 대한 전반적인 개요와 함께 Qt5 개발자에게 어떻게 문의할 수 있는지도 안내합니다.


서문
====

.. rubric:: 역사

Qt4는 2005년 이후로 발전을 거듭하는 동안 수많은 애플리케이션의 기초가 되었고 데스크탑과 모바일 시스템을 지탱하는 기반을 제공했습니다. 최근 몇년 동안 컴퓨터 사용자의 이용 패턴은 데스크탑 PC에서 노트북으로, 최근에는 모바일 기기로 바뀌었습니다. 전통적인 데스크탑 환경은 점점 더 인터넷과 연결된 터치 기반의 모바일 기기로 대체되고 있습니다. 이러한 변화와 함께 우리는 그동안 우리를 지배해 온 Windows UI에서 벗어나, 다른 UI 언어로 구현된 다른 형태의 기기를 이용하는데 점점 더 많은 시간을 보내고 있습니다.

Qt4는 여러 데스크탑 OS에서 실행 가능한 하나의 통일된 UI 위젯을 제공하기 위해 설계되었습니다. Qt 사용자의 요구는 시대의 흐름에 따라 변화되어 이제는 사용자 중심의 터치 기반 인터페이스를 구현하고, 주요 데스크탑 OS 뿐만 아니라 모바일 환경에서도 새로운 UI의 구현을 필요로 하고 있습니다. 이러한 고객의 요구에 기반하여, 완전히 새로운 UI를 구현할 수 있도록 해주는 일련의 UI 컴포넌트가 Qt Quick이라는 이름으로 Qt 4.7부터 소개 되었습니다.

Qt5의 특징
----------

Qt5는 성공적이었던 Qt4를 완전히 새로 고친 전면 개정판입니다. Qt 4.8은 Qt4가 출시된 지 거의 7년 후에 배포되었습니다. (역자 주: Qt4.0은 2005년 출시, Qt4.8은 2011년 출시) 이제 이 놀라운 툴킷을 더욱 멋지게 만들 때가 되었습니다. Qt5의 주요 특징은 다음과 같습니다.

* **뛰어난 그래픽 성능**: Scene graph를 기반으로 한 Qt Quick 2 렌더링 구조는 OpenGL (ES)로 구현되었습니다. 새로 구현한 그래픽 스택을 통해 새로운 차원의 그래픽 효과를 쉽게 구현할 수 있게 되었습니다.

* **개발자의 생산성**: QML과 자바스크립트는 UI 작성을 위한 주요 수단입니다. 그 기반은 C++에 의해 구동됩니다. 자바스크립트와 C++의 분리는 프론트엔드 개발자가 멋진 사용자 인터페이스를 만드는 데 집중하고 백엔드 C++ 개발자는 안정성, 성능 및 런타임을 향상시키는데 중점을 둘 수 있도록 해줍니다.

* **크로스플랫폼 이식성**: 통합된 Qt 플랫폼 추상화(Qt Platform Abstraction: QPA)를 통해 Qt를 좀 더 쉽고 빠르게 더 넓은 범위의 플랫폼에 이식할 수 있게 되었습니다. Qt5는 Qt Essentials과 Add-ons으로 구성되어 있으며, 이를 통해 OS 개발자가 필수 모듈에 집중할 수 있게 해주고 Qt 구동에 필요한 런타임을 좀 더 작게 만들 수 있게 되었습니다.

* **오픈 소스 프로젝트**: Qt는 이제 `qt.io <http://qt.io>`_ 에서 호스팅되는 진정한 개방형 관리 프로젝트입니다. 오픈 소스 프로젝트이고 개발 과정은 커뮤니티에 의해 움직입니다.



Qt5 소개
========


Qt Quick
--------

Qt Quick은 Qt5 만의 사용자 인터페이스 관련 기술을 통칭하는 용어입니다. Qt Quick 그 자체는 아래와 같은 여러 기술들의 집합입니다.

* QML - 사용자 인터페이스를 위한 마크업 언어(markup language)
* JavaScript - 동적 스크립트 언어
* Qt C++ - 높은 이식성을 가진 향상된 C++ 라이브러리

.. figure:: assets/qt5_overview.png


HTML과 유사하게 QML은 일종의 마크업 언어입니다. 하나의 QML 파일은 Qt Quick에서 element라고 불리는 태그들을 다음에 같이 중괄호 안에 나열하는 것으로 구성됩니다 (``Item {}``). 이러한 구조는 사용자 인터페이스를 구현하기 위해 완전히 새롭게 디자인된 것이고, 개발자에게 빠른 개발 속도과 높은 가독성을 제공합니다. 자바스크립트 코드를 이용해 사용자 인터페이스에 동적인 요소나 개발자의 로직을 더할 수 있습니다. 그리고 Qt C++를 통해 Qt Quick을 확장하는 방식으로 여러분이 구현하고자 하는 기능 요소를 쉽게 추가할 수 있습니다. 이렇게 선언적으로 구현하는 UI를 프론트 엔드(front-end)라 부르고 네이티브 코드로 구현한 부분을 백엔드(back-end)라고 부릅니다. 이러한 구조는 여러분의 응용 프로그램에서 많은 컴퓨팅 파워를 요구하거나 네이티브 코드로 동작해야 하는 기능 요소를 사용자 인터페이스 부분에서 분리할 수 있도록 해줍니다.


일반적인 프로젝트에서 프론트 엔드는 QML과 자바스크립트로 개발하고, 시스템과의 인터페이스나 무거운 작업을 담당하는 백엔드 코드는 Qt C++을 이용해 개발합니다. 이러한 구조로 인해 개발자의 업무가 디자인 구현과 기능 구현으로 자연스럽게 나뉘게 됩니다. 일반적으로 백엔드는 Qt 자체의 유닛 테스트 프레임워크를 통해 검증된 후에 실제로 사용되기 위해 프론트엔드 개발자에게 전달됩니다.


사용자 인터페이스 구현해보기
----------------------------

Qt Quick을 사용해 간단한 사용자 인터페이스를 구현해보면서 QML의 특징을 살펴봅시다. 목표는 아래와 같이 바람개비가 돌아가는 종이 바람개비를 만드는 것입니다.


.. figure:: assets/scene.png
    :scale: 50%


``main.qml`` 이라는 이름의 빈 문서에서 시작해보겠습니다. 모든 QML 파일의 이름은 ``.qml`` 로 끝나야 합니다. HTML 같은 다른 마크업 언어와 마찬가지로 하나의 QML 파일은 오직 하나의 root element를 가져야 합니다. 우리의 경우에는 배경 이미지와 같은 너비와 높이를 가진 ``Image`` element가 root element입니다.

.. code-block:: qml

    import QtQuick 2.5

    Image {
        id: root
        source: "images/background.png"
    }

QML에서 어떤 element 타입도 root element가 될 수 있습니다. 우리는 배경 이미지의 경로를 source property로 가진 ``Image`` element를 root element로 사용했습니다.


.. figure:: src/showcase/images/background.png


.. note::

    각각의 element는 property를 가집니다. 예를 들어 image는 ``width`` 와 ``height`` 뿐만 아니라 ``source`` 와 같은 property도 가지고 있습니다. Image element의 크기는 해당 이미지의 크기에 따라 자동으로 정해집니다. 아니면 ``width`` 와 ``height`` property에 적절한 픽셀값을 설정할 수도 있습니다.

    가장 기본적인 element들은 우리가 첫번째 줄에 import문으로 명시한 ``QtQuick`` 모듈에 존재합니다.

    ``id`` 라는 특별한 property가 있습니다. 이 property는 선택사항이며 해당 element를 문서의 다른 곳에서 가리키는 식별자 역할을 합니다. 중요: ``id`` property는 지정된 후에는 변경될 수 없으며 실행 중에 할당될 수 없습니다. Root element의 id로 ``root`` 를 사용하는 것은 저자의 습관일 뿐이며 긴 QML 문서에서 id를 일일이 확인하지 않아도 최상위 element를 참고한다는 것을 쉽게 짐작할 수 있게 해줍니다.

이제 배경 위에 막대와 바람개비를 추가해보겠습니다. 각각은 아래와 같은 이미지입니다.

.. figure:: src/showcase/images/pole.png
.. figure:: src/showcase/images/pinwheel.png

막대는 배경 이미지의 수평 중심에 위치하고 막대의 끝은 이미지 하단과 맞닿아있어야 합니다. 그리고 바람개비는 배경 이미지의 정중앙에 위치하면 됩니다.

일반적으로 사용자 인터페이스는 본 예제의 경우처럼 image element만 사용되는 것이 아니라, 다른 많은 element type들의 조합으로 만들어집니다.


.. code-block:: qml

  Image {
      id: root
      ...
      Image {
          id: pole
          anchors.horizontalCenter: parent.horizontalCenter
          anchors.bottom: parent.bottom
          source: "images/pole.png"
      }

      Image {
          id: wheel
          anchors.centerIn: parent
          source: "images/pinwheel.png"
      }
      ...
  }



바람개비를 가운데 위치시키기 위해 ``anchor`` 라는 다소 복잡해보이는 property를 사용해보겠습니다. Anchoring은 부모 객체와 자식 객체 간의 상대적인 위치를 지정할 수 있도록 해줍니다. 예를 들어 ``anchors.centerIn: parent`` 라는 구문은 어떤 객체를 부모 객체의 중앙에 위치시킨다는 의미입니다. 두 오브젝트에 대해서 left, right, top, bottom, centerIn, fill, verticalCenter, horizontalCenter 등의 관계를 설정할 수 있습니다. 물론 두 객체의 property는 서로 쌍이 맞아야 합니다. 오브젝트의 왼쪽을 다른 오브젝트의 위쪽에 오도록 설정하는 것은 말이 안 되니까요.

이제 우리는 바람개비를 부모 객체인 배경 이미지의 중심에 오도록 설정했습니다.

.. note::

    경우에 따라 위치를 정중앙에서 조금만 이동시킬 필요도 있을 겁니다. ``anchors.horizontalCenterOffset`` 이나 ``anchors.verticalCenterOffset`` 으로 이러한 미세 조정이 가능합니다. 다른 모든 achors에 대해서도 이와 유사하게 offset을 부여할 수 있는 property가 있습니다. Anchors property 전체 리스트를 문서에서 확인해보세요.

.. note::

    이미지를 root element (이 예제에서는 ``Image`` element)의 자식 element로 위치시키는 것은 선언적 언어(declarative language)의 중요한 개념을 보여줍니다. 여러분이 레이어(layer)를 어떤 순서로 나열하고 어떻게 그룹을 이루게 했는지에 따라 사용자 인터페이스가 결정됩니다. 최상위 레이어(사각 형태겠죠)가 먼저 그려지고, 자식 레이어는 그 레이어가 속한 element의 내부 좌표 공간을 기준으로 그 위에 그려집니다.

예제를 좀 더 재밌게 만들어보기 위해 사용자 입력에 반응하는 요소를 추가해 보겠습니다. 아이디어는 마우스로 화면 아무 곳이나 클릭하면 바람개비가 돌아가는 것입니다.


마우스 입력을 받기 위해 ``MouseArea`` element를 사용하고 그 영역을 root element만큼 크게 설정하겠습니다.

.. code-block:: qml

    Image {
        id: root
        ...
        MouseArea {
            anchors.fill: parent
            onClicked: wheel.rotation += 90
        }
        ...
    }

마우스 영역은 해당 영역 안에서 사용자가 클릭하면 시그널(signal)을 발생시킵니다. 여러분은 ``onClicked`` 라는 함수를 override해서 이 시그널에 반응하는 코드를 작성할 수 있습니다. 예제의 경우에는 바람개비 이미지에 접근해서 90도 시계방향으로 회전시키고 있습니다.

.. note::

    이러한 동작은 모든 시그널에 적용됩니다. 이 때 함수의 이름은 ``on`` + ``SignalName`` 와 같은 규칙을 따릅니다. 또한 모든 property는 그 값이 변경될 때 시그널이 발생하는데, 그 때의 이름 규칙은 다음과 같습니다.

        ``on`` + ``PropertyName`` + ``Changed``

    예를 들어 ``width`` property가 변경되고 있다면 ``onWidthChanged: print(width)`` 와 같은 구문을 통해 변경되는 값을 관찰할 수 있습니다.

이제 바람개비가 돌아갈 것입니다. 하지만 아직 그렇게 부드럽게 돌아가진 않네요. Rotation property가 즉시 변하기 때문입니다. 일정한 시간을 두고 90도씩 property가 바뀐다면 좋겠죠. 이제 애니메이션이 필요한 때가 되었습니다. 애니메이션은 어떤 property의 값이 특정 시간 동안 어떻게 변화하는지를 정의하는 것입니다. 여기서는 behavior라는 property를 통해 애니메이션을 적용해보겠습니다. ``Behavior`` 는 지정된 property가 변경될 때마다 적용할 애니메이션을 지정하는 것입니다. 간단히 말해서 property의 값이 바뀔 때마다 애니메이션이 동작합니다. 이 방법은 QML로 애니메이션을 정의하는 여러 방법 중 하나입니다.

.. code-block:: qml

    Image {
        id: root
        Image {
            id: wheel
            Behavior on rotation {
                NumberAnimation {
                    duration: 250
                }
            }
        }
    }

이제 wheel의 rotation property가 바뀔 때마다 ``NumberAnimation`` 을 통한 정의에 따라 250ms 동안 wheel이 움직일 것입니다. 그래서 매번 90도씩 돌아가는데 250ms의 시간이 소요됩니다.

.. figure:: assets/scene2.png
    :scale: 50%

.. note:: 여러분이 실행한 화면에서 실제로 바람개비가 흐릿하지는 않을 것입니다. 위 화면은 단지 바람개비의 회전을 나타내고자 한 것일 뿐입니다. 하지만 assets 폴더에 흐릿한 바람개비가 있습니다. 호기심이 생기신다면 한 번 적용해보세요.


이제 바람개비가 충분히 그럴듯해진 것 같네요. Qt Quick 프로그래밍이 어떤 방식으로 이루어지는지 감을 잡는데 이 예제가 도움이 되었길 바랍니다.

Qt의 구성 요소 (building blocks)
================================

Qt5는 여러 모듈로 구성됩니다. 일반적으로 하나의 모듈은 개발자가 사용할 수 있는 라이브러리를 뜻합니다. 그 중 일부 모듈은 Qt가 지원되는 플랫폼에 필수적인 요소입니다. 그러한 모듈을 묶어서 *Qt 핵심 모듈(Qt Essentials Modules)* 이라 부릅니다. 그 외 다른 많은 모듈들은 옵션이며 *Qt 애드온 모듈(Qt Add-On Modules)* 을 구성합니다. 대다수의 개발자에게는 그다지 사용할 필요가 없는 것처럼 보일 수도 있지만, SW 개발에 있어서 공통적으로 접할 수 있는 문제를 해결해주는 솔루션이기 때문에 알아두면 좋을 것입니다.

Qt 모듈
-------

Qt 핵심 모듈(Qt Essentials modules)은 Qt를 지원하는 플랫폼에 필수적인 요소입니다. 그리고 Qt Quick 2를 이용한 Qt5 응용 프로그램을 개발하기 위한 기초를 제공합니다.

.. rubric:: 핵심 모듈 (Core-Essential Modules)

QML 프로그래밍을 시작하기 위한 Qt5 모듈의 최소 집합.

.. list-table::
    :widths: 20 80
    :header-rows: 1

    *   - 모듈명
        - 설명
    *   - Qt Core
        - 다른 모듈에 사용되는 핵심 비 그래픽(non-graphical) 클래스.
    *   - Qt GUI
        - GUI 컴포넌트를 위한 기반 클래스. OpenGL도 포함.
    *   - Qt Multimedia
        - 오디오, 비디오, 라디오, 카메라 기능을 위한 클래스.
    *   - Qt Network
        - 네트워크 프로그래밍을 더 쉽고 이식성 있게 해주는 클래스.
    *   - Qt QML
        - QML과 자바스크립트 언어를 위한 클래스.
    *   - Qt Quick
        - 맞춤형 사용자 인터페이스를 가진 고도로 동적인 응용 프로그램을 위한 선언적인 프레임워크.
    *   - Qt SQL
        - SQL을 사용하는 데이터베이스 연동을 위한 클래스.
    *   - Qt Test
        - Qt 응용 프로그램과 라이브러리의 유닛 테스트(unit test)를 위한 클래스.
    *   - Qt WebKit
        - WebKit2 기반 구현 및 새로운 QML API. 애드온 모듈(add-on modules)에서 Qt WebKit Widgets를 참조.
    *   - Qt WebKit Widgets
        - Qt4에서 이어져 온 WebKit1 및 QWidget 기반 클래스.
    *   - Qt Widgets
        - C++ 위젯으로 Qt GUI를 확장하기 위한 클래스.


.. digraph:: essentials

    QtGui -> QtCore
    QtNetwork ->QtCore
    QtMultimedia ->QtGui
    QtQml -> QtCore
    QtQuick -> QtQml
    QtSql -> QtCore


.. rubric:: Qt 애드온 모듈 (Qt Addon Modules)

핵심 모듈(essential modules) 외에 Qt는 소프트웨어 개발자를 위한 추가 모듈을 제공합니다. 사용가능한 애드온 모듈의 간략한 목록은 아래와 같습니다.

* Qt 3D - 3D 그래픽 프로그래밍을 쉽고 선언적인 방식으로 가능하게 해주는 API의 집합.
* Qt Bluetooth - 블루투스(Bluetooth) 무선 기술을 사용하는 플랫폼을 위한 C++와 QML API.
* Qt Contacts - 주소록/연락처 데이터베이스에 접근하기 위한 C++ and QML API
* Qt Location - QML과 C++ 인터페이스를 통한 위치 정보, 지도, 내비게이션, 장소 검색 기능. 위치 정보를 위한 NMEA 백엔드
* Qt Organizer -  일정 관리자의 이벤트(할일, 약속 등등)에 접근하기 위한 C++와 QML API
* Qt Publish and Subscribe
* Qt Sensors - QML과 C++ 인터페이스를 통한 센서 접근.
* Qt Service Framework -  응용 프로그램이 알림 메시지를 읽고 탐색하고 수신하는 기능 제공.
* Qt System Info - 시스템 관련 정보와 성능.
* Qt Versit - vCard와 iCalendar 포맷 지원
* Qt Wayland - 리눅스 전용 모듈. Wayland 서버를 위한 Qt Compositor API와 클라이언트용 Wayland 플랫폼 플러그인
* Qt Feedback - 사용자 동작에 대한 햅틱 및 오디오 피드백.
* Qt JSON DB - Qt용 non-SQL 오브젝트 저장소.

.. note::

    이러한 모듈들은 Qt 배포판에 포함되지 않기 때문에 각 모듈마다 얼마나 많은 개발자가 활발히 참여하는지와 얼마나 잘 테스트 되는지에 따라 그 상태가 다릅니다. (역자 주: 본 문서에는 애드온 모듈을 배포 버전에 포함되는지 여부로 구분하고 있지만 일반적으로는 핵심 모듈이 아닌 다른 모든 Qt 모듈들을 애드온이라고 부릅니다.)

지원 플랫폼
-----------

Qt는 다양한 종류의 플랫폼을 지원합니다. 모든 주요 데스크탑, 임베디드 플랫폼이 지원됩니다. 여러분의 고유한 플랫폼에 Qt가 필요하다면 Qt 플랫폼 추상화 (Qt Platform Abraction: QPA)를 통해서 이전보다 쉽게 Qt를 이식할 수 있습니다.

하나의 플랫폼에 대해 Qt5를 테스트하는 것은 많은 시간을 필요로 하는 일입니다. 그래서 Qt 프로젝트에서는 일종의 레퍼런스 플랫폼을 선정했습니다. 이러한 플랫폼은 최상의 코드 품질을 보장하기 위해 시스템 테스트를 통해 면밀히 테스트됩니다. 하지만 이것을 명심해주세요. 오류 없는 코드는 없습니다.




Qt 프로젝트
===========

`Qt 프로젝트 위키 <http://wiki.qt.io/>`_ 에서 발췌합니다.

"Qt 프로젝트는 Qt에 관심있는 개발자로 구성된 코드 중심의 합의 기반 커뮤니티입니다. Qt에 흥미가 있다면 누구나 커뮤니티에 참여해서 의사 결정 과정에 관여하고 Qt의 개발에 기여할 수 있습니다."

Qt 프로젝트는 Qt의 오픈 소스 부분을 개발하는 조직입니다. 이 프로젝트는 다른 사용자가 Qt에 기여할 수 있는 기반을 제공합니다. 가장 많이 기여한 곳은 Qt의 상업적 권리를 보유하고 있는 DIGIA(역자 주: 현재는 The Qt Company)입니다.

기업에 대해서 Qt는 오픈 소스의 측면과 상업적인 측면을 가지고 있습니다. 상업적 측면은 오픈 소스 라이센스를 준수할 수 없거나 준수하지 않을 회사를 위한 것입니다. 이러한 상업적 측면이 없다면 이러한 기업은 Qt를 사용할 수 없을 것이며 DIGIA는 Qt 프로젝트에 그렇게 많은 코드를 기여하지 못할 것입니다.

전세계적으로 Qt를 사용해 여러 플랫폼에서 제품을 개발하고 컨설팅을 제공하는 많은 회사들이 있습니다. Qt를 주요 개발 라이브러리로 사용하는 많은 오픈 소스 프로젝트와 오픈 소스 개발자들이 있습니다. 이렇게 역동적인 커뮤니티의 일원이 되고 훌륭한 개발 도구와 라이브러리로 개발한다는 것은 멋진 일인 것 같습니다. 여러분도 Qt와 함께 더욱 멋진 사람이 될 수 있을까요? 아마도 그럴 겁니다. :-)

**여기서부터 시작하세요: http://wiki.qt.io/**
