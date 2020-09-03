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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0df05e7363db01bd4f16fee5d75141dc93df1c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710267"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Spécifie les indicateurs d'hôte IntelliSense.

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
|`IHF_READONLYCONTEXT`|La mémoire tampon de contexte est en lecture seule.|
|`IHF_NOSEPARATESUBJECT`|Aucun texte d’objet. La mémoire tampon de contexte contient IntelliSense-Target (implique `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|Le texte de l’objet ne prend pas en charge plusieurs lignes.|
|`IHF_FORCECOMMITTOCONTEXT`|Comme pour `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|La modification (dans l’objet ou le contexte) doit être effectuée en mode de Refrappe.|

## <a name="requirements"></a>Configuration requise
 SingleFileeditor. idl

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.TextManager.Interop>
