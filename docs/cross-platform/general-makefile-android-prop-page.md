---
title: "Propriétés générales du projet (makefile Android C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: fa380209cb18862eb9bf782141d62befd79c5644
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="general-project-properties-android-c-makefile"></a>Propriétés générales du projet (makefile Android C++)

Propriété | Description | Options
--- | ---| ---
Répertoire de sortie | Spécifie un chemin relatif vers le répertoire de fichiers de sortie ; peut inclure des variables d’environnement.
Répertoire intermédiaire | Spécifie un chemin relatif vers le répertoire de fichiers intermédiaire ; peut inclure des variables d’environnement.
Fichier journal de génération | Spécifie le fichier journal de génération à utiliser quand la journalisation de la génération est activée.
Type de configuration | Spécifie le type de sortie générée par cette configuration. | **Bibliothèque dynamique (.so)** : bibliothèque dynamique (.so)<br>**Bibliothèque statique (.a)** : bibliothèque statique (.a)<br>**Utilitaire** : utilitaire<br>**Makefile** : fichier makefile<br>
