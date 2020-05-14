---
title: IntelliSenseHostFlags - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
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
|`IHF_READONLYCONTEXT`|Le mémoire tampon est lu uniquement.|
|`IHF_NOSEPARATESUBJECT`|Pas de texte de sujet. Mémoire tampon contient IntelliSense-cible `!IHF_READONLYCONTEXT`(implique ).|
|`IHF_SINGLELINESUBJECT`|Le texte sujet n’est pas multi-lignes-capable.|
|`IHF_FORCECOMMITTOCONTEXT`|Identique à `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|L’édition (en sujet ou en contexte) doit se faire en mode surtype.|

## <a name="requirements"></a>Spécifications
 SingleFileeditor.idl

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.TextManager.Interop>
