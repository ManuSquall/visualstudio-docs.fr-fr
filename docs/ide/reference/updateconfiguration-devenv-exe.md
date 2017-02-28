---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 3
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 741deb2d7ddb86e0a0dc0246b1c53f497d0ab5f8
ms.lasthandoff: 02/22/2017

---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
Notifie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour qu’il fusionne les packages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sur le système et vérifie si des modifications ont été apportées au cache MEF.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] exécute cette commande automatiquement quand vous installez un package VSIX. Vous devez exécuter `devenv.exe /updateconfiguration` après la mise à jour corrective de vos fichiers pour que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mette à jour le cache MEF. Cela vous permet d’évaluer si votre correctif est adapté.  
  
## <a name="example"></a>Exemple  
 La ligne de commande suivante permet à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de fusionner les packages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sur le système et de vérifier si des modifications ont été apportées au cache MEF.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
