---
title: Ouvrir et enregistrer des éléments de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c406e66b1008f0bb2aad95a427e1329d4269f1f6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948806"
---
# <a name="opening-and-saving-project-items"></a>Ouverture et enregistrement d’éléments de projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lorsque vous ajoutez un nouveau type de projet, vous devez gérer l’ouverture et l’enregistrement de vos fichiers de projets dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’environnement de développement intégré (IDE). Les rubriques suivantes décrivent les différentes approches pour ouvrir et enregistrer des fichiers.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Affichage de fichiers à l’aide de la commande Ouvrir un fichier](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Fournit une explication pas à pas de la façon dont l’IDE gère le **ouvrir un fichier** commande et le rôle de projets dans la réponse à cette commande.  
  
 [Affichage de fichiers à l’aide de la commande Ouvrir avec](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Fournit une explication détaillée, étape par étape de la façon dont l’IDE gère le **ouvrir avec** commande, demande l’ouverture d’un fichier qui a le choix des éditeurs standards.  
  
 [Guide pratique pour Ouvrez éditeurs spécifiques du projet](../../extensibility/how-to-open-project-specific-editors.md)  
 Fournit des instructions détaillées permettant de spécifier que les fichiers d’un type particulier dans votre projet doivent être ouvert à l’aide d’un éditeur spécifique au projet.  
  
 [Guide pratique pour Ouvrir des éditeurs Standard](../../extensibility/how-to-open-standard-editors.md)  
 Fournit des instructions détaillées pour la spécification de l’activation de l’IDE ouvrir un éditeur standard pour les fichiers dans votre type de projet.  
  
 [Guide pratique pour Ouvrir des éditeurs pour les Documents ouverts](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Fournit des instructions détaillées pour ouvrir un éditeur spécifique au projet pour un fichier ouvert.  
  
 [Enregistrement d’un document standard](../../extensibility/internals/saving-a-standard-document.md)  
 Fournit une explication détaillée de la façon dont l’IDE gère le **enregistrer**, **enregistrer en tant que**, et **Enregistrer tout** commandes pour un document ouvert dans un éditeur standard.  
  
 [Enregistrement d’un document personnalisé](../../extensibility/internals/saving-a-custom-document.md)  
 Fournit un diagramme et une explication détaillée de la façon dont l’IDE gère le **enregistrer**, **enregistrer en tant que**, et **Enregistrer tout** commandes pour les documents ouverts dans un éditeur personnalisé.  
  
 [Déterminer quel éditeur ouvre un fichier dans un projet](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Décrit le processus qui l’IDE suit pour sélectionner l’éditeur approprié ou le concepteur pour un fichier.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’éditeurs et de concepteurs personnalisés](../../extensibility/creating-custom-editors-and-designers.md)  
 Répertorie les quatre types d’éditeurs que l’IDE peut héberger et donne les descriptions de chaque éditeur.  
  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Explique comment les projets contrôlent la façon dont le code est compilé et généré, mode d’ouverture des éditeurs, et comment les éléments de projet sont mis en forme.
