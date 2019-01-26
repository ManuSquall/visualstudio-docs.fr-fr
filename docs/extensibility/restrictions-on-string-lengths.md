---
title: Restrictions relatives aux longueurs de chaîne | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 679737b9590cd018f0de16298391351aedb0ac94
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929950"
---
# <a name="restrictions-on-string-lengths"></a>Restrictions relatives aux longueurs de chaîne
L’API de plug-in de contrôle de Source de limite les longueurs des chaînes utilisées dans les différentes fonctions.  
  
## <a name="string-length-values"></a>Valeurs de longueur de chaîne  
  
|Constante|Value|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  Longueur n’inclut pas la fin `null`. Autres constantes avec un suffixe « _Taille » au lieu de « _LEN » n’incluent pas d’espace pour le point final `null`.  
  
|Constante|Value|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)