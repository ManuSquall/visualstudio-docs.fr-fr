---
title: "Propriétés de l’éditeur de liens Clang (Android C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 2b4ca3f4c67315357343d1803bda12f11d8cbc6d
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="clang-linker-properties-android-c"></a>Propriétés de l’éditeur de liens Clang (Android C++)

Propriété | Description | Options
--- | ---| ---
Fichier de sortie | L’option substitue le nom et l’emplacement par défaut du programme créé par l’éditeur de liens. (-o)
Afficher la progression | Affiche les messages de progression de l’éditeur de liens.
Version | L’option -version indique à l’éditeur de liens de placer un numéro de version dans l’en-tête de l’exécutable.
Activer la sortie détaillée | L’option -verbose indique à l’éditeur de liens de générer la sortie des messages détaillés pour le débogage.
Activation des liens incrémentiels | L’option indique à l’éditeur de liens d’activer l’édition des liens incrémentielle.
Chemin de recherche de la bibliothèque partagée | Permet à l’utilisateur de remplir le chemin de recherche de la bibliothèque partagée.
Répertoires de bibliothèques supplémentaires | Permet à l’utilisateur de substituer le chemin de la bibliothèque d’environnement. (-L folder).
Signaler les références de symboles non résolus | Quand cette option est activée, les références des symboles non résolus sont signalées.
Optimiser pour l’utilisation de la mémoire | Permet d’optimiser l’utilisation de la mémoire, en relisant les tables de symboles selon les besoins.
Bibliothèques par défaut spécifiques ignorées | Spécifie un ou plusieurs noms de bibliothèques par défaut à ignorer.
Références des symboles forcées | Force l’entrée du symbole dans le fichier de sortie en tant que symbole non défini.
Informations de symboles du débogueur | Informations de symboles du débogueur contenues dans le fichier de sortie. | **Inclure tout**<br>**Omettre les symboles superflus pour le traitement du réadressage**<br>**Omettre les informations de symboles du débogueur uniquement**<br>**Omettre toutes les informations de symbole**<br>
Empaqueter les informations de symboles du débogueur | Supprimez les informations relatives aux symboles du débogueur avant d’effectuer l’empaquetage.  Une copie de la ressource binaire d’origine est utilisée pour le débogage.
Nom de fichier du mappage | L’option Map indique à l’éditeur de liens de créer un fichier de mappage avec le nom spécifié par l’utilisateur.
Marquer les variables ReadOnly après le réadressage | Cette option marque les variables en lecture seule après le réadressage.
Activer la liaison de fonction immédiate | Cette option marque l’objet pour une liaison de fonction immédiate.
Nécessiter une pile exécutable | Cette option marque la sortie en indiquant qu’elle ne nécessite pas de pile exécutable.
Archive complète | L’archive complète utilise l’ensemble du code des sources et des dépendances supplémentaires.
Options supplémentaires | Options supplémentaires.
Dépendances supplémentaires | Spécifie les éléments supplémentaires à ajouter à la ligne de commande de l’éditeur de liens.
Dépendances de bibliothèque | Cette option permet de spécifier des bibliothèques supplémentaires à ajouter à la ligne de commande de l’éditeur de liens. Les bibliothèques supplémentaires sont ajoutées à la fin de la ligne de commande de l’éditeur de liens. Elles commencent par 'lib' et finissent par l’extension '.a' ou '.so'.  (-lFILE)
