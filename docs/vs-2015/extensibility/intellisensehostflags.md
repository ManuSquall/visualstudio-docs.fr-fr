---
title: IntelliSenseHostFlags | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12945998b215e9082591fad514bd9c16ab789405
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948664"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie les indicateurs d’hôte IntelliSense.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
  
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
 <xref:Microsoft.VisualStudio.TextManager.Interop>
