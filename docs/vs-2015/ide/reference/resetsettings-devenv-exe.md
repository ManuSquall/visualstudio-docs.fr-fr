---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1b35026140b424da0f7fa71cb9e70b72c3dba243
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689657"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Restaure les paramètres par défaut de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et lance automatiquement l’IDE [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Réinitialise éventuellement les paramètres avec les valeurs d’un fichier .vssettings spécifié.  
  
 Les paramètres par défaut sont déterminés par le profil sélectionné quand [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a été lancé pour la première fois.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Arguments  
 `SettingsFile`  
 Chemin complet et nom du fichier .vssettings à appliquer à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Pour restaurer le profil des paramètres de développement généraux, utilisez `General`.  
  
## <a name="remarks"></a>Remarques  
 Si aucun `SettingsFile` n’est spécifié, vous êtes invité à sélectionner une collection de paramètres par défaut au prochain démarrage de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Exemple  
 La ligne de commande suivante applique les paramètres stockés dans le fichier `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
