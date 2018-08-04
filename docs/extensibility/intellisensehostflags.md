---
title: IntelliSenseHostFlags | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 582dc76bfd8b76ffa4d3664ab3e28f95fe2cef50
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500012"
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
 <xref:Microsoft.VisualStudio.TextManager.Interop>