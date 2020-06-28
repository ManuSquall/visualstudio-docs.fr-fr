---
title: IDiaSymbol::get_undecoratedNameEx | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 25942c76d8e568d6354c9a6a2b2c69c806cde352
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461601"
---
# <a name="idiasymbolget_undecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Récupère une partie ou l’intégralité d’un nom non décoré pour un nom décoré C++ (liaison).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_undecoratedNameEx( 
   DWORD undecorateOptions,
   BSTR* pRetval
);
```

#### <a name="parameters"></a>Paramètres
 `undecoratedOptions`

dans Spécifie une combinaison d’indicateurs qui contrôlent ce qui est retourné. Consultez la section Notes pour connaître les valeurs spécifiques et ce qu’elles font.

 `pRetVal`

à Retourne le nom non décoré pour un nom décoré C++.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques
 `undecorateOptions`Peut être une combinaison des indicateurs suivants.

> [!NOTE]
> Les noms des indicateurs ne sont pas définis dans le kit de développement logiciel (SDK) DIA. vous devez donc ajouter les déclarations à votre code ou utiliser les valeurs brutes.

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|UNDNAME_COMPLETE|0x0000|Active l’indécoration complète.|
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Supprime les traits de soulignement de début des mots clés étendus Microsoft.|
|UNDNAME_NO_MS_KEYWORDS|0x0002|Désactive l’expansion des mots clés étendus Microsoft.|
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Désactive l’expansion du type de retour pour la déclaration principale.|
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Désactive l’expansion du modèle de déclaration.|
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Désactive l’expansion du spécificateur de langage de déclaration.|
|UNDNAME_RESERVED1|0x0020|RÉSERVÉ.|
|UNDNAME_RESERVED2|0x0040|RÉSERVÉ.|
|UNDNAME_NO_THISTYPE|0x0060|Désactive tous les modificateurs sur le `this` type.|
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Désactive l’expansion des spécificateurs d’accès pour les membres.|
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Désactive l’expansion de « Throw-signatures » pour les fonctions et les pointeurs vers les fonctions.|
|UNDNAME_NO_MEMBER_TYPE|0x0200|Désactive l’expansion des `static` membres ou `virtual` .|
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Désactive l’expansion du modèle Microsoft pour les retours UDT.|
|UNDNAME_32_BIT_DECODE|0x0800|Décore les noms décorés de 32 bits.|
|UNDNAME_NAME_ONLY|0x1000|Obtient uniquement le nom de la déclaration principale ; retourne simplement [Scope ::] Name.  Développe les paramètres de modèle.|
|UNDNAME_TYPE_ONLY|0x2000|L’entrée est simplement un encodage de type. compose un déclarateur abstrait.|
|UNDNAME_HAVE_PARAMETERS|0x4000|Les paramètres de modèle réels sont disponibles.|
|UNDNAME_NO_ECSU|0x8000|Supprime enum/class/struct/union.|
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Supprime la vérification des caractères d’identificateur valides.|
|UNDNAME_NO_PTR64|0x20000|N’inclut pas ptr64 dans la sortie.|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)