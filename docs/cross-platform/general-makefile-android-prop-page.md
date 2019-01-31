---
title: Propriétés générales du projet (makefile Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
author: corob
ms.author: mblome
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: ee398add6b0cca8288d82cd090e1abef07a40d23
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041761"
---
# <a name="general-project-properties-android-c-makefile"></a>Propriétés générales du projet (Makefile Android C++)

Property | Description | Options
--- | ---| ---
Répertoire de sortie | Spécifie un chemin relatif vers le répertoire de fichiers de sortie ; peut inclure des variables d’environnement.
Répertoire intermédiaire | Spécifie un chemin relatif vers le répertoire de fichiers intermédiaire ; peut inclure des variables d’environnement.
Fichier journal de génération | Spécifie le fichier journal de génération à utiliser quand la journalisation de la génération est activée.
Type de configuration | Spécifie le type de sortie générée par cette configuration. | **Bibliothèque dynamique (.so)** : bibliothèque dynamique (*.so*)<br>**Bibliothèque statique (.a)** : bibliothèque statique (*.a*)<br>**Utilitaire** : utilitaire<br>**Makefile** : fichier makefile<br>
