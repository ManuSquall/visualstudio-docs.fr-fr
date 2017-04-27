---
title: "Paramètres de projet VC++, Projets et solutions, boîte de dialogue Options | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 15
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: fbe834e4e8178a129f68cec1c4a78ffea3c9fd7c
ms.lasthandoff: 04/25/2017

---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Paramètres de projet VC++, Projets et solutions, boîte de dialogue Options
Cette boîte de dialogue vous permet de définir des paramètres du projet [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] relatifs à la journalisation de la génération et à la prise en charge des types de fichiers.  
  
### <a name="to-access-this-dialog-box"></a>Pour accéder à cette boîte de dialogue  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Sélectionnez **Projets et solutions**, puis **Paramètres de projet VC++**.  
  
## <a name="build-customization-search-path"></a>Chemin de recherche des personnalisations de la build  
 Spécifie la liste des répertoires contenant les fichiers .rules, qui vous permettent de définir des règles de génération pour vos projets.  
  
## <a name="build-logging"></a>Journalisation de la génération  
 **Oui**  
 Active la création du fichier journal de génération. Cette option génère le fichier BuildLog.htm, qui se trouve dans le répertoire des fichiers intermédiaires du projet. Chaque nouvelle génération remplace le fichier BuildLog.htm précédent.  
  
 **Non**  
 Désactive la création du fichier journal de génération.  
  
## <a name="build-timing"></a>Minutage de la génération  
 **Oui**  
 Active le minutage de la génération. Si vous sélectionnez cette option, la durée de la génération est enregistrée dans la fenêtre Sortie. Pour plus d’informations, consultez [Fenêtre Sortie](../../ide/reference/output-window.md).  
  
 **Non**  
 Désactive le minutage de la génération.  
  
## <a name="extensions-to-hide"></a>Extensions à masquer  
 Spécifie les extensions de noms des fichiers qui ne s’affichent pas dans l’**Explorateur de solutions** quand l’option **Afficher tous les fichiers** est activée.  
  
## <a name="extensions-to-include"></a>Extensions à inclure  
 Spécifie les extensions de noms des fichiers qui peuvent être portés dans votre projet.  
  
## <a name="maximum-concurrent-c-compilations"></a>Nombre maximal de compilations C++ simultanées  
 Spécifie le nombre maximal de cœurs de processeur à utiliser pour la compilation C++ parallèle.  
  
## <a name="show-environment-in-log"></a>Affichage de l’environnement dans le journal  
 **Oui**  
 Répertorie les variables d’environnement dans le fichier journal de génération. Cette option indique de répercuter toutes les variables d’environnement, lors de la génération de projets [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], dans le fichier journal de génération.  
  
 **Non**  
 Exclut les variables d’environnement du fichier journal de génération.  
  
## <a name="solution-explorer-mode"></a>Mode Explorateur de solutions  
 **Afficher uniquement les fichiers du projet**  
 Configure l’**Explorateur de solutions** de sorte qu’il n’affiche que les fichiers du projet.  
  
 **Afficher tous les fichiers**  
 Configure l’**Explorateur de solutions** de sorte qu’il affiche les fichiers du projet et les fichiers sur disque dans le dossier du projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération de programmes C/C++](/cpp/build/building-c-cpp-programs)   
 [Référence de la génération C/C++](/cpp/build/reference/c-cpp-building-reference)
