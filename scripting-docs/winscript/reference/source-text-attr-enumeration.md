---
title: Source_text_attr, énumération | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05faeddf43c91ce0f45d54d2f6b6ed46cf8d2a4f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157985"
---
# <a name="sourcetextattr-enumeration"></a>SOURCE_TEXT_ATTR, énumération
Décrit les attributs d'un caractère unique de texte source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Value|Description|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|Le caractère fait partie d’un mot clé de langage, par exemple, le mot clé VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Le caractère fait partie d’un bloc de commentaire.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Le caractère ne fait pas partie du texte source de langage compilé. Par exemple, le HTML qui entoure un bloc de script.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Le caractère fait partie d’un opérateur de langage. Par exemple :, l’opérateur arithmétique **+**.|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Le caractère fait partie d’une constante numérique de langage.  Par exemple, la constante 3,141 59 par défaut.|  
|SOURCETEXT_ATTR_STRING|0x0020|Le caractère fait partie d’une constante de chaîne de langage. Par exemple, la chaîne « Hello World ».|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Le caractère indique le début d’un bloc (fonction)|  
  
## <a name="remarks"></a>Notes  
 En règle générale, le `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, et `IActiveScriptDebug::GetScriptTextAttributes` méthodes retournent un seul attribut de texte par caractère, à moins que :  
  
-   L’indicateur GETATTRTYPE_DEPSCAN est défini, auquel cas la méthode peut retourner les indicateurs SOURCETEXT_ATTR_IDENTIFIER et SOURCETEXT_ATTR_MEMBERLOOKUP,  
  
-   L’indicateur GETATTRFLAG_THIS est défini, auquel cas la méthode peut retourner l’indicateur SOURCETEXT_ATTR_THIS,  
  
-   L’indicateur GETATTRFLAG_HUMANTEXT est défini, auquel cas la méthode peut retourner l’indicateur SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)