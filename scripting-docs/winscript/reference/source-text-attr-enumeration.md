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
ms.openlocfilehash: f34121ca50ae2467addb29809e7a3792063642ec
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60062448"
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
  
- L’indicateur GETATTRTYPE_DEPSCAN est défini, auquel cas la méthode peut retourner les indicateurs SOURCETEXT_ATTR_IDENTIFIER et SOURCETEXT_ATTR_MEMBERLOOKUP,  
  
- L’indicateur GETATTRFLAG_THIS est défini, auquel cas la méthode peut retourner l’indicateur SOURCETEXT_ATTR_THIS,  
  
- L’indicateur GETATTRFLAG_HUMANTEXT est défini, auquel cas la méthode peut retourner l’indicateur SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)