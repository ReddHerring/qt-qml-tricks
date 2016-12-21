set(QT_SUPERMACROS_SRC
	)
	
set(QT_QML_MODELS_SRC
	qt-qml-models/QQmlObjectListModel.cpp
	qt-qml-models/QQmlObjectListModel.h
	qt-qml-models/QQmlVariantListModel.cpp
	qt-qml-models/QQmlVariantListModel.h
	#qt-qml-models/QtQmlModelsDefines.h
)	
set(QT_QML_TRICKS_DIR ${CMAKE_CURRENT_SOURCE_DIR})
set(QT_QML_TRICKS_INCLUDES ${QT_QML_TRICKS_DIR}/qt-supermacros ${QT_QML_TRICKS_DIR}/qt-qml-models CACHE VECTOR "Qt-Qml-Tricks includes")
add_library(qt-qml-tricks SHARED ${QT_SUPERMACROS_SRC}  ${QT_QML_MODELS_SRC} )
TARGET_INCLUDE_DIRECTORIES(	qt-qml-tricks
							PUBLIC ${QT_QML_TRICKS_DIR}
							PUBLIC ${QT_QML_TRICKS_INCLUDES})
target_link_libraries(qt-qml-tricks Qt5::Core Qt5::Gui Qt5::Qml )
INSTALL(TARGETS qt-qml-tricks
		LIBRARY DESTINATION ${IPO_INSTALL_DESTINATION} COMPONENT ${IPO_INSTALL_COMPONENT}
		RUNTIME DESTINATION ${IPO_INSTALL_DESTINATION} COMPONENT ${IPO_INSTALL_COMPONENT}
		ARCHIVE DESTINATION ${IPO_INSTALL_DESTINATION} COMPONENT ${IPO_INSTALL_COMPONENT}_static
)