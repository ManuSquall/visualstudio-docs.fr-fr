---
title: NameSearchOptions | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ceadd085a3099721e73e04dd09ea5a0b81ad1d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
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