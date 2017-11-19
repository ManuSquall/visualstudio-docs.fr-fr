---
title: "Ouvrir et enregistrer des éléments de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a30589591a7cef60ecfb19945366f8fcf539da02
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="opening-and-saving-project-items"></a>Ouvrir et enregistrer des éléments de projet
Lorsque vous ajoutez un nouveau type de projet, vous devez gérer l’ouverture et l’enregistrement de vos fichiers de projets dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Les rubriques suivantes décrivent les différentes approches pour ouvrir et enregistrer des fichiers.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Affichage de fichiers à l’aide de la commande Ouvrir un fichier](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Fournit une explication pas à pas comment l’IDE gère le **ouvrir le fichier** commande et le rôle de projets dans la réponse à cette commande.  
  
 [Affichage de fichiers à l’aide de la commande Ouvrir avec](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Fournit une explication détaillée, étape par étape comment l’IDE gère le **ouvrir avec** commande, demander l’ouverture d’un fichier qui a des choix d’éditeurs standards.  
  
 [Guide pratique pour ouvrir des éditeurs spécifiques à un projet](../../extensibility/how-to-open-project-specific-editors.md)  
 Fournit des instructions pas à pas permettant de spécifier que les fichiers d’un type particulier dans votre projet doivent être ouvert à l’aide d’un éditeur spécifique au projet.  
  
 [Guide pratique pour ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)  
 Fournit des instructions détaillées pour la spécification de l’activation de l’IDE ouvrir un éditeur standard pour les fichiers dans votre type de projet.  
  
 [Guide pratique pour ouvrir des éditeurs pour les documents ouverts](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Fournit des instructions pas à pas pour ouvrir un éditeur spécifique au projet pour un fichier ouvert.  
  
 [Enregistrement d’un document standard](../../extensibility/internals/saving-a-standard-document.md)  
 Fournit une explication détaillée de la façon dont l’IDE gère le **enregistrer**, **enregistrer en tant que**, et **Enregistrer tout** commandes pour un document ouvert dans un éditeur standard.  
  
 [Enregistrement d’un document personnalisé](../../extensibility/internals/saving-a-custom-document.md)  
 Fournit un schéma et une explication détaillée de la façon dont l’IDE gère le **enregistrer**, **enregistrer en tant que**, et **Enregistrer tout** commandes pour les documents ouverts dans un éditeur personnalisé.  
  
 [Déterminer quel éditeur ouvre un fichier dans un projet](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Décrit le processus par l’IDE suit pour sélectionner l’éditeur approprié ou du concepteur pour un fichier.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’éditeurs et de concepteurs personnalisés](../../extensibility/creating-custom-editors-and-designers.md)  
 Répertorie les quatre types d’éditeurs que l’IDE peut héberger et donne les descriptions de chaque éditeur.  
  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Explique comment les projets contrôlent la façon dont le code est compilé et intégré, mode d’ouverture des éditeurs et comment les éléments de projet sont mis en forme.