


configure_file(config-highcontrast.h.cmake ${CMAKE_CURRENT_BINARY_DIR}/config-highcontrast.h )

set(Highcontrast_SRCS
    animations/highcontrastanimation.cpp
    animations/highcontrastanimations.cpp
    animations/highcontrastanimationdata.cpp
    animations/highcontrastbaseengine.cpp
    animations/highcontrastbusyindicatordata.cpp
    animations/highcontrastbusyindicatorengine.cpp
    animations/highcontrastdialdata.cpp
    animations/highcontrastdialengine.cpp
    animations/highcontrastenabledata.cpp
    animations/highcontrastgenericdata.cpp
    animations/highcontrastheaderviewdata.cpp
    animations/highcontrastheaderviewengine.cpp
    animations/highcontrastscrollbardata.cpp
    animations/highcontrastscrollbarengine.cpp
    animations/highcontrastspinboxengine.cpp
    animations/highcontrastspinboxdata.cpp
    animations/highcontraststackedwidgetdata.cpp
    animations/highcontraststackedwidgetengine.cpp
    animations/highcontrasttabbarengine.cpp
    animations/highcontrasttabbardata.cpp
    animations/highcontrasttoolboxengine.cpp
    animations/highcontrasttransitiondata.cpp
    animations/highcontrasttransitionwidget.cpp
    animations/highcontrastwidgetstateengine.cpp
    animations/highcontrastwidgetstatedata.cpp
    debug/highcontrastwidgetexplorer.cpp
    highcontrastaddeventfilter.cpp
    highcontrasthelper.cpp
    highcontrastmnemonics.cpp
    highcontrastpropertynames.cpp
    highcontrastsplitterproxy.cpp
    highcontraststyle.cpp
    highcontraststyleplugin.cpp
    highcontrasttileset.cpp
    highcontrastwindowmanager.cpp
    fakehighcontraststyleconfigdata.cpp
)
add_definitions(-DQT_PLUGIN)

include_directories(
    ${QT_INCLUDES}
    ${CMAKE_CURRENT_BINARY_DIR}
    .
    animations
    debug
)

set(LIBRARY_NAME "highcontrast-qt${QT_VERSION_NUMBER}")

add_library(${LIBRARY_NAME} MODULE ${Highcontrast_SRCS})
target_link_libraries(${LIBRARY_NAME} ${QT_QTCORE_LIBRARY} ${QT_QTGUI_LIBRARY} ${QT_QTDBUS_LIBRARY})
set_target_properties(${LIBRARY_NAME} PROPERTIES
    LINK_FLAGS "-Wl,--no-undefined"
    LIBRARY_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}"
    OUTPUT_NAME "highcontrast"
    PREFIX "")

install(TARGETS ${LIBRARY_NAME} DESTINATION "${QT_STYLE_PATH}/")
