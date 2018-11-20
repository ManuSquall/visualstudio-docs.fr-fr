---
title: IDiaSymbol::get_undecoratedNameEx | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e1902c6300a35924e7fcd626d9b63f69bc5bbc2c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745409"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nom de (liaison) de décoré de tout ou partie de l’extrait d’un nom non décoré pour C++.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `undecoratedOptions`  
 [in] Spécifie une combinaison d’indicateurs qui contrôlent ce qui est retourné. Consultez la section Notes pour les valeurs spécifiques et ce qu’ils font.  
  
 `pRetVal`  
 [out] Retourne que le nom non décoré pour C++ de nom décoré.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
 Le `undecorateOptions` peut être une combinaison des indicateurs suivants.  
  
> [!NOTE]
>  Les noms de l’indicateur ne sont pas définis dans le SDK DIA, donc vous devez ajouter les déclarations à votre code ou d’utiliser les valeurs brutes.  
  
|Indicateur|Valeur|Description|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Permet d’undecoration complète.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0 x 0001|Supprime des traits de soulignement de début à partir de l’étendue des mots clés de Microsoft.|  
|UNDNAME_NO_MS_KEYWORDS|0 x 0002|Désactive l’expansion de l’étendue des mots clés de Microsoft.|  
|UNDNAME_NO_FUNCTION_RETURNS|0 x 0004|Désactive l’expansion du type de retour pour une déclaration principale.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Désactive l’expansion du modèle de déclaration.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Désactive l’expansion du spécificateur de langage de déclaration.|  
|UNDNAME_RESERVED1|0x0020|RÉSERVÉ.|  
|UNDNAME_RESERVED2|0 x 0040|RÉSERVÉ.|  
|UNDNAME_NO_THISTYPE|0x0060|Désactive tous les modificateurs sur la `this` type.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0 x 0080|Désactive l’expansion de spécificateurs d’accès pour les membres.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Désactive l’expansion de « throw signatures » pour les fonctions et les pointeurs vers des fonctions.|  
|UNDNAME_NO_MEMBER_TYPE|0 x 0200|Désactive l’expansion de `static` ou `virtual` membres.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0 x 0400|Désactive l’expansion du modèle Microsoft pour retourne UDT.|  
|UNDNAME_32_BIT_DECODE|0 x 0800|Undecorates noms décorés 32 bits.|  
|UNDNAME_NAME_ONLY|0 x 1000|Obtient uniquement le nom de déclaration principal ; retourne simplement [étendue ::] nom.  Développe un modèle params.|  
|UNDNAME_TYPE_ONLY|0 x 2000|L’entrée est simplement un type de codage ; compose un déclarateur abstrait.|  
|UNDNAME_HAVE_PARAMETERS|0 x 4000|Les paramètres de modèle réels sont disponibles.|  
|UNDNAME_NO_ECSU|0 x 8000|Supprime l’enum/classe/struct/union.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0 x 10000|Supprime la vérification des caractères d’identificateur valide.|  
|UNDNAME_NO_PTR64|0 x 20000|N’inclut pas de ptr64 dans la sortie.|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



