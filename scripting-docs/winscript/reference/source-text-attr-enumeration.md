---
title: "SOURCE_TEXT_ATTR, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SOURCE_TEXT_ATTR (constantes)"
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# SOURCE_TEXT_ATTR, &#233;num&#233;ration
Décrivez les attributs d'un caractère unique de texte source.  
  
## Syntaxe  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR  
{  
    SOURCETEXT_ATTR_KEYWORD    = 0x0001,  
    SOURCETEXT_ATTR_COMMENT    = 0x0002,  
    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,  
    SOURCETEXT_ATTR_OPERATOR   = 0x0008,  
    SOURCETEXT_ATTR_NUMBER    = 0x0010,  
    SOURCETEXT_ATTR_STRING    = 0x0020,  
    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040  
};  
  
```  
  
## Membres  
  
|Membre|Valeur|Description|  
|------------|------------|-----------------|  
|SOURCETEXT\_ATTR\_KEYWORD|0x0001|Le caractère fait partie d'un mot clé de langage, par exemple, le mot clé `While`VBScript.|  
|SOURCETEXT\_ATTR\_COMMENT|0x0002|Le caractère fait partie d'un bloc de commentaires.|  
|SOURCETEXT\_ATTR\_NONSOURCE|0x0004|Le caractère ne fait pas partie de texte source compilé de langage.  Par exemple, HTML entourant un bloc de script.|  
|SOURCETEXT\_ATTR\_OPERATOR|0x0008|Le caractère fait partie d'un opérateur de langage.  Par exemple : , l'opérateur arithmétique **\+**.|  
|SOURCETEXT\_ATTR\_NUMBER|0x0010|Le caractère fait partie d'une constante numérique de langage.  Par exemple, les 3,14159 constants.|  
|SOURCETEXT\_ATTR\_STRING|0x0020|Le caractère fait partie d'une constante de chaîne SQL.  Par exemple, la chaîne « Hello World ».|  
|SOURCETEXT\_ATTR\_FUNCTION\_START|0x0040|Le caractère indique le début d'un bloc de fonction|  
  
## Notes  
 En général, `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, et les méthodes d' `IActiveScriptDebug::GetScriptTextAttributes` retournent un attribut de texte par caractère, à moins que :  
  
-   La balise de GETATTRTYPE\_DEPSCAN est définie dans ce cas, la méthode peut retourner les balises de SOURCETEXT\_ATTR\_IDENTIFIER et de SOURCETEXT\_ATTR\_MEMBERLOOKUP,  
  
-   La balise de GETATTRFLAG\_THIS est définie dans ce cas, la méthode peut retourner la balise de SOURCETEXT\_ATTR\_THIS,  
  
-   La balise de GETATTRFLAG\_HUMANTEXT est définie dans ce cas, la méthode peut retourner la balise de SOURCETEXT\_ATTR\_HUMANTEXT.  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)