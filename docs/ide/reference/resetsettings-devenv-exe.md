---
title: "-ResetSettings (devenv.exe) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 52d01cfc3ae6a453330c2dda5da137f449ff5cbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
Restaure les paramètres par défaut de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et lance automatiquement l’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Réinitialise éventuellement les paramètres avec les valeurs d’un fichier .vssettings spécifié.  
  
 Les paramètres par défaut sont déterminés par le profil sélectionné quand [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a été lancé pour la première fois.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Arguments  
 `SettingsFile`  
 Chemin complet et nom du fichier .vssettings à appliquer à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Pour restaurer le profil des paramètres de développement généraux, utilisez `General`.  
  
## <a name="remarks"></a>Notes  
 Si aucun `SettingsFile` n’est spécifié, vous êtes invité à sélectionner une collection de paramètres par défaut au prochain démarrage de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="example"></a>Exemple  
 La ligne de commande suivante applique les paramètres stockés dans le fichier `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)