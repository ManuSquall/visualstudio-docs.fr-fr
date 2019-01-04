---
title: Éléments d’un modèle de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ee628d56094026b588c76451c143158000636a5c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962608"
---
# <a name="elements-of-a-project-model"></a>Éléments d’un modèle de projet
Les interfaces et les implémentations de tous les projets de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] partagent une structure de base : le modèle de projet pour votre type de projet. Dans votre modèle de projet, qui est le VSPackage que vous développez, vous créez des objets qui sont conformes avec vos décisions de conception et l’implication des fonctionnalités globales fournies par l’IDE. Bien que vous contrôlez le mode de conservation d’un élément de projet, par exemple, vous ne contrôlez pas notification qu’un fichier doit être persistante. Lorsqu’un utilisateur met l’accent sur un élément de projet ouvert et choisit **enregistrer** sur le **fichier** menu sur le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu barre, votre code de type de projet doit intercepter la commande à partir de l’IDE, conserve le fichier, et envoyer la notification à l’IDE que le fichier est modifié n’est plus.  
  
 Votre VSPackage interagit avec l’IDE via les services qui fournissent l’accès aux interfaces IDE. Par exemple, grâce à des services particuliers, vous moniteur et l’itinéraire commandes et fournissez des informations de contexte pour les sélections effectuées dans le projet. Toutes les fonctionnalités IDE globale nécessaire pour votre VSPackage sont fournie par les services. Pour plus d’informations sur les services, consultez [Comment : Obtenir un service](../../extensibility/how-to-get-a-service.md).  
  
 Autres considérations relatives à la mise en œuvre :  
  
- Un modèle de projet unique peut contenir plusieurs types de projet.  
  
- Types de projets et les fabriques de surveillance du projet sont enregistrés indépendamment avec GUID.  
  
- Chaque projet doit avoir un fichier de modèle ou un Assistant pour initialiser le nouveau fichier de projet lorsqu’un utilisateur crée un nouveau projet via la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur. Par exemple, le [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modèles initialiser ce que deviennent des fichiers .vcproj.  
  
  L’illustration suivante montre les interfaces principales, les services et les objets qui composent une implémentation de projet standard. Vous pouvez utiliser l’application d’assistance de l’application, `HierUtil7`, pour créer les objets sous-jacents et autres réutilisable de programmation. Pour plus d’informations sur la `HierUtil7` application d’assistance de l’application, consultez [HierUtil7 de l’utilisation des classes de projet pour implémenter un type de projet (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
  ![Graphique modèle de projet Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
  modèle de projet  
  
  Pour plus d’informations sur les interfaces et les services répertoriés dans le diagramme précédent et les autres interfaces facultatives ne pas inclus dans le diagramme, consultez [les composants de base de modèle de projet](../../extensibility/internals/project-model-core-components.md).  
  
  Projets peut prendre en charge les commandes et par conséquent doit implémenter le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface pour participer au routage des commandes via le GUID de contexte de commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Créer des types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Utiliser des classes de projet HierUtil7 pour implémenter un type de projet (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Composants principaux du modèle projet](../../extensibility/internals/project-model-core-components.md)   
 [Créer des instances de projet à l’aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Guide pratique pour Bénéficiez d’un service](../../extensibility/how-to-get-a-service.md)   
 [Créer des types de projets](../../extensibility/internals/creating-project-types.md)
