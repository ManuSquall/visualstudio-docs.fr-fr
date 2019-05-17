---
title: IDiaSymbol::get_undecoratedNameEx | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c50f5d352d8a52b0eb8b125992b2c325e48234
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386781"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Nom de (liaison) de décoré de tout ou partie de l’extrait d’un nom non décoré pour C++.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_undecoratedNameEx( 
   DWORD undecorateOptions,
   BSTR* pRetval
);
```

#### <a name="parameters"></a>Paramètres
 `undecoratedOptions`

[in] Spécifie une combinaison d’indicateurs qui contrôlent ce qui est retourné. Consultez la section Notes pour les valeurs spécifiques et ce qu’ils font.

 `pRetVal`

[out] Retourne le nom non décoré pour un C++ nom décoré.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 Le `undecorateOptions` peut être une combinaison des indicateurs suivants.

> [!NOTE]
> Les noms de l’indicateur ne sont pas définis dans le SDK DIA, donc vous devez ajouter les déclarations à votre code ou d’utiliser les valeurs brutes.

|Indicateur|Value|Description|
|----------|-----------|-----------------|
|UNDNAME_COMPLETE|0x0000|Permet d’undecoration complète.|
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Supprime des traits de soulignement de début à partir de l’étendue des mots clés de Microsoft.|
|UNDNAME_NO_MS_KEYWORDS|0x0002|Désactive l’expansion de l’étendue des mots clés de Microsoft.|
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Désactive l’expansion du type de retour pour une déclaration principale.|
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Désactive l’expansion du modèle de déclaration.|
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Désactive l’expansion du spécificateur de langage de déclaration.|
|UNDNAME_RESERVED1|0x0020|RÉSERVÉ.|
|UNDNAME_RESERVED2|0x0040|RÉSERVÉ.|
|UNDNAME_NO_THISTYPE|0x0060|Désactive tous les modificateurs sur la `this` type.|
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Désactive l’expansion de spécificateurs d’accès pour les membres.|
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Désactive l’expansion de « throw signatures » pour les fonctions et les pointeurs vers des fonctions.|
|UNDNAME_NO_MEMBER_TYPE|0x0200|Désactive l’expansion de `static` ou `virtual` membres.|
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Désactive l’expansion du modèle Microsoft pour retourne UDT.|
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates noms décorés 32 bits.|
|UNDNAME_NAME_ONLY|0x1000|Obtient uniquement le nom de déclaration principal ; retourne simplement [étendue ::] nom.  Développe un modèle params.|
|UNDNAME_TYPE_ONLY|0x2000|L’entrée est simplement un type de codage ; compose un déclarateur abstrait.|
|UNDNAME_HAVE_PARAMETERS|0x4000|Les paramètres de modèle réels sont disponibles.|
|UNDNAME_NO_ECSU|0x8000|Supprime l’enum/classe/struct/union.|
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Supprime la vérification des caractères d’identificateur valide.|
|UNDNAME_NO_PTR64|0x20000|N’inclut pas de ptr64 dans la sortie.|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)