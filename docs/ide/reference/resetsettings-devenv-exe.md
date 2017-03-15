---
title: "/ResetSettings (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/ResetSettings (commutateur de Devenv)"
  - "Devenv, /ResetSettings (commutateur)"
  - "ResetSettings (commutateur)"
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Restaure les paramètres par défaut de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et lance automatiquement l'IDE de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Éventuellement, réinitialise les paramètres avec les valeurs d'un fichier .vssettings spécifié.  
  
 Les paramètres par défaut sont déterminés par le profil sélectionné quand [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a été lancé pour la première fois.  
  
## Syntaxe  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## Arguments  
 `SettingsFile`  
 Le chemin d'accès complet et le nom du fichier .vssettings à appliquer à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Pour restaurer le profil des paramètres de développement généraux, utilisez `General`.  
  
## Notes  
 Si aucun `SettingsFile` n'est spécifié, vous êtes invité à sélectionner une collection de paramètres par défaut au prochain démarrage de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Exemple  
 La ligne de commande suivante applique les paramètres stockés dans le fichier `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## Voir aussi  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)