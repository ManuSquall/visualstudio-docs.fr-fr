---
title: NameSearchOptions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6d721ebc5849fc459d24173ad0500b4b1c12260f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182977"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spécifie les options de recherche pour les noms de symboles et de fichiers.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## <a name="elements"></a>Éléments  
 `nsNone`  
 Aucune option n'est spécifiée.  
  
 `nsfCaseSensitive`  
 Applique une correspondance de nom respectant la casse.  
  
 `nsfCaseInsensitive`  
 Applique une correspondance de nom ne respectant pas la casse.  
  
 `nsfFNameExt`  
 Traite les noms comme des chemins d’accès et applique une correspondance de nom de nom de fichier. ext.  
  
 `nsfRegularExpression`  
 Applique une correspondance de nom respectant la casse à l’aide d’astérisques (*) et de points d’interrogation ( ?) comme caractères génériques.  
  
 `nsfUndecoratedName`  
 S’applique uniquement aux symboles qui ont des noms non décorés et décorés.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de cette énumération sont passées aux méthodes suivantes :  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2. h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession :: Findchildren (](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession :: findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
