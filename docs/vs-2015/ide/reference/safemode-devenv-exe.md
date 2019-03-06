---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4c1cd4b15c3ce3462d6d49eca39fedbc64c744c7
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54767300"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Démarre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en mode sans échec, en chargeant uniquement l’environnement et les services par défaut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Remarques  
 Ce commutateur empêche le chargement de tous les packages VS tiers au démarrage de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], garantissant ainsi la stabilité de l’exécution.  
  
## <a name="description"></a>Description  
 L’exemple suivant démarre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en mode sans échec.  
  
## <a name="code"></a>Code  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
