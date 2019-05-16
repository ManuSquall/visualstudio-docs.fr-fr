---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2f20463cd91148143a1d3fb7f7de5cc1649d683c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689335"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Notifie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour qu’il fusionne les packages [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sur le système et vérifie si des modifications ont été apportées au cache MEF.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Remarques  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] exécute cette commande automatiquement quand vous installez un package VSIX. Vous devez exécuter `devenv.exe /updateconfiguration` après la mise à jour corrective de vos fichiers pour que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mette à jour le cache MEF. Cela vous permet d’évaluer si votre correctif est adapté.  
  
## <a name="example"></a>Exemple  
 La ligne de commande suivante permet à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] de fusionner les packages [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sur le système et de vérifier si des modifications ont été apportées au cache MEF.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
