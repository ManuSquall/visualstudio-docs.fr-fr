---
title: Projets et solutions, boîte de dialogue Options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1294de78e93709bc60cd94be97613f032725bf5c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758199"
---
# <a name="projects-and-solutions-options-dialog-box"></a>Projets et solutions, boîte de dialogue Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Définit le chemin par défaut des dossiers du projet [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et détermine le comportement par défaut de la fenêtre **Sortie**, de la **Liste des tâches** et de l’**Explorateur de solutions** au fur et à mesure que les projets sont développés et générés. Pour accéder à cette boîte de dialogue, cliquez sur **Outils / Options**, développez **Projets et solutions**, puis cliquez sur **Général**.  
  
> [!NOTE]
>  Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition. Cette page d’aide concerne les **Paramètres de développement généraux**. Pour afficher ou modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="settings"></a>Paramètres  
 **Emplacement des projets**  
 Définit l’emplacement par défaut où sont créés les projets et les répertoires et dossiers de solution. Plusieurs boîtes de dialogue utilisent aussi l'emplacement défini dans cette option comme point de démarrage des dossiers. Par exemple, la boîte de dialogue Ouvrir un projet utilise cet emplacement pour le raccourci Mes projets.  
  
 **Emplacement des modèles des projets utilisateur**  
 Définit l’emplacement par défaut utilisé par la boîte de dialogue **Nouveau projet** pour créer la liste de **Mes modèles**. Pour plus d’informations, consultez [Guide pratique pour localiser et organiser les modèles](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Emplacement des modèles des éléments utilisateur**  
 Définit l’emplacement par défaut utilisé par la boîte de dialogue **Ajouter un nouvel élément** pour créer la liste de **Mes modèles**. Pour plus d’informations, consultez [Guide pratique pour localiser et organiser les modèles](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Toujours afficher la liste d’erreurs à la fin de la génération avec erreurs**  
 Ouvre la fenêtre **Liste d’erreurs** à l’achèvement de build, uniquement en cas d’échec de la génération du projet. Les erreurs qui se produisent pendant le processus de génération sont affichées. Lorsque cette option est désactivée, les erreurs persistent, mais la fenêtre ne s'ouvre pas quand la génération est terminée. Cette option est activée par défaut.  
  
 **Suivre un élément actif dans l’Explorateur de solutions**  
 Quand l’option est sélectionnée, l’**Explorateur de solutions** s’ouvre automatiquement et l’élément actif est sélectionné. L'élément sélectionné change au fur et à mesure que vous utilisez différents fichiers dans un projet ou une solution, ou différents composants dans un concepteur. Quand cette option est désactivée, la sélection de l’**Explorateur de solutions** ne change pas automatiquement. Cette option est activée par défaut.  
  
 **Afficher les configurations de build avancées**  
 Quand cette option est sélectionnée, les options de configuration de build apparaissent dans les boîtes de dialogue **Pages de propriétés du projet** et **Pages de propriétés de la solution**. Si l’option est désactivée, les options de configuration de build n’apparaissent pas dans les boîtes de dialogue **Pages de propriétés du projet** et **Pages de propriétés de la solution** pour les projets [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] et [!INCLUDE[csprcs](../../includes/csprcs-md.md)] qui contiennent une seule configuration ou les deux configurations debug et release. Si un projet possède une configuration définie par l'utilisateur, les options de configuration de build sont affichées.  
  
 Si l’option n’est pas sélectionnée, les commandes du menu **Générer**, telles que **Générer la solution**, **Régénérer la solution** et **Nettoyer la solution**, sont exécutées sur la configuration Release et les commandes du menu **Déboguer**, telles que **Démarrer le débogage** et **Exécuter sans débogage**, sont exécutées sur la configuration Debug.  
  
 **Toujours afficher la solution**  
 Lorsque cette option est sélectionnée, la solution et toutes les commandes qui agissent sur les solutions sont toujours affichées dans l'IDE. Lorsqu'elle est désactivée, tous les projets sont créés comme projets autonomes. En outre, vous ne voyez pas la solution dans l'Explorateur de solutions ou les commandes qui agissent sur les solutions dans l'IDE si la solution contient un seul projet.  
  
 **Enregistrer les nouveaux projets lors de leur création**  
 Quand cette option est sélectionnée, vous pouvez spécifier un emplacement pour votre projet dans la boîte de dialogue **Nouveau projet**. Lorsqu'elle est désactivée, tous les nouveaux projets sont créés en tant que projets temporaires. Lorsque vous travaillez avec des projets temporaires, vous pouvez créer un projet et l'expérimenter sans avoir à spécifier un emplacement sur le disque.  
  
 **Prévenir l’utilisateur lorsque l’emplacement du projet n’est pas fiable**  
 Si vous tentez de créer un projet ou d’ouvrir un projet existant dans un emplacement qui n’est pas totalement fiable (par exemple, un chemin UNC ou un chemin HTTP), un message s’affiche. Utilisez cette option pour spécifier si le message s'affiche chaque fois que vous essayez de créer ou d'ouvrir un projet dans un emplacement qui n'est pas entièrement fiable.  
  
 **Afficher la fenêtre Sortie au démarrage de la génération**  
 Affiche automatiquement la fenêtre Sortie dans l'IDE au démarrage des générations de la solution. Pour plus d’informations, consultez [How to: Control the Output Window](http://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858) (Guide pratique pour contrôler la fenêtre Sortie). Cette option est activée par défaut.  
  
 **Inviter à utiliser des noms symboliques au moment de renommer les fichiers**  
 Lorsque cette option est sélectionnée, un message s'affiche et demande si [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] doit également renommer toutes les références du projet à l'élément de code.  
  
## <a name="see-also"></a>Voir aussi  
 [Options (boîte de dialogue), Projets et solutions, Générer et exécuter](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
