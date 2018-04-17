---
title: NameSearchOptions | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 32a5858d52f7d5ee2adfce48084fd096c4dae0a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="namesearchoptions"></a>NameSearchOptions
Spécifie les options de recherche pour les noms de fichiers et de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
enum NameSearchOptions {   
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
 Applique une correspondance de nom qui respecte la casse.  
  
 `nsfCaseInsensitive`  
 Applique une correspondance de nom sans respecter la casse.  
  
 `nsfFNameExt`  
 Traite les noms en tant que chemins d’accès et s’applique à une correspondance de nom nomfichier.ext.  
  
 `nsfRegularExpression`  
 Applique une correspondance de nom respectant la casse à l’aide d’astérisques (*) et les points d’interrogation ( ?) comme caractères génériques.  
  
 `nsfUndecoratedName`  
 S’applique uniquement aux symboles qui ont à la fois non décorés et les noms décorés.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de cette énumération sont passés aux méthodes suivantes :  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Spécifications  
 En-tête : dia2.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)