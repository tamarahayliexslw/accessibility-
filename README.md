# accessibility-
consolewrite("Action 4a" &amp; @CRLF) $oChromeAddressBar=_UIA_getObjectByFindAll($oChromeToolbar, $cAddressBarByName  , $treescope_subtree) ;works in chrome 29 if not isobj($oChromeAddressbar) Then findThemAll($oChromeToolbar,$treescope_subtree) EndIf   $t=stringsplit(_UIA_getPropertyValue($oChromeAddressBar, $UIA_BoundingRectanglePropertyId),";") _DrawRect($t[1],$t[3]+$t[1],$t[2],$t[4]+$t[2]) _UIA_action($oChromeAddressBar,"leftclick")     consolewrite("Action 4b" &amp; @CRLF) ;~ give some time to open website sleep(2000) $oDocument=_UIA_getFirstObjectOfElement($oChrome,"controltype:=" &amp; $UIA_DocumentControlTypeId , $treescope_subtree) if not isobj($oDocument) Then findThemAll($oChrome,$treescope_subtree) Else $t=stringsplit(_UIA_getPropertyValue($oDocument, $UIA_BoundingRectanglePropertyId),";") _DrawRect($t[1],$t[3]+$t[1],$t[2],$t[4]+$t[2]) EndIf   sleep(500)   consolewrite("Action 4c retrieve document after clicking a hyperlink" &amp; @CRLF) $oForumLink=_UIA_getObjectByFindAll($oDocument,"name:=On", $treescope_subtree) if not isobj($oForumLink) Then consolewrite("*** Scripting will fail as accessibility is off ****") MsgBox(4096, "Accessibility warning", "Accessibility is turned off, put it on by clicking on Off after Global accessibility mode", 10) findThemAll($oDocument,$treescope_subtree) EndIf
