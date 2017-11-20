---
title: "Source_text_attr, énumération | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f21bbfacc4918ff0e67731d5efd5521f371cbdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="sourcetextattr-enumeration"></a>SOURCE_TEXT_ATTR, énumération
Décrit les attributs d'un caractère unique de texte source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Valeur|Description|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0 x 0001|Le caractère fait partie d’un mot clé de langage, par exemple, le mot clé de VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0 x 0002|Le caractère fait partie d’un bloc de commentaire.|  
|SOURCETEXT_ATTR_NONSOURCE|0 x 0004|Le caractère n’est pas partie du texte source de langage compilé. Par exemple, le HTML qui entoure un bloc de script.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Le caractère fait partie d’un opérateur de langage. Par exemple :, l’opérateur arithmétique  **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Le caractère fait partie d’une constante numérique.  Par exemple, la constante 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Le caractère fait partie d’une constante de chaîne de langue. Par exemple, la chaîne « Hello World ».|  
|SOURCETEXT_ATTR_FUNCTION_START|0 x 0040|Le caractère indique le début d’un bloc (fonction)|  
  
## <a name="remarks"></a>Remarques  
 En règle générale, les `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, et `IActiveScriptDebug::GetScriptTextAttributes` méthodes retournent un seul attribut de texte par caractère, à moins que :  
  
-   L’indicateur GETATTRTYPE_DEPSCAN est défini, auquel cas la méthode peut retourner les indicateurs SOURCETEXT_ATTR_IDENTIFIER et SOURCETEXT_ATTR_MEMBERLOOKUP,  
  
-   L’indicateur GETATTRFLAG_THIS est défini, auquel cas la méthode peut retourner l’indicateur SOURCETEXT_ATTR_THIS,  
  
-   L’indicateur GETATTRFLAG_HUMANTEXT est défini, auquel cas la méthode peut retourner l’indicateur SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)