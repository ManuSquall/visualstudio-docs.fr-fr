---
title: IntelliSenseHostFlags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d0e66f70b91985882df5691d05175995b4f6ca8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328077"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Spécifie les indicateurs d’hôte IntelliSense.

## <a name="syntax"></a>Syntaxe

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>Paramètres

|Membres|Description|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Mémoire tampon de contexte est en lecture seule.|
|`IHF_NOSEPARATESUBJECT`|Aucun texte de l’objet. Mémoire tampon de contexte contient la cible d’IntelliSense (implique `!IHF_READONLYCONTEXT`).|
|`IHF_SINGLELINESUBJECT`|Texte de l’objet n’est pas multi-ligne prenant en charge.|
|`IHF_FORCECOMMITTOCONTEXT`|Comme pour `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|Modification (dans l’objet ou le contexte) doit être effectuée en mode Refrappe.|

## <a name="requirements"></a>Configuration requise
 SingleFileeditor.idl

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.TextManager.Interop>