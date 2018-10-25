---
title: Éléments d’un modèle de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c062ce943e2ee42cd90877827ab7b92ee33c871b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883651"
---
# <a name="elements-of-a-project-model"></a>Éléments d’un modèle de projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les interfaces et les implémentations de tous les projets de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] partagent une structure de base : le modèle de projet pour votre type de projet. Dans votre modèle de projet, qui est le VSPackage que vous développez, vous créez des objets qui sont conformes avec vos décisions de conception et l’implication des fonctionnalités globales fournies par l’IDE. Bien que vous contrôlez le mode de conservation d’un élément de projet, par exemple, vous ne contrôlez pas notification qu’un fichier doit être persistante. Lorsqu’un utilisateur met l’accent sur un élément de projet ouvert et choisit **enregistrer** sur le **fichier** menu sur le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] menu barre, votre code de type de projet doit intercepter la commande à partir de l’IDE, conserve le fichier, et envoyer la notification à l’IDE que le fichier est modifié n’est plus.  
  
 Votre VSPackage interagit avec l’IDE via les services qui fournissent l’accès aux interfaces IDE. Par exemple, grâce à des services particuliers, vous moniteur et l’itinéraire commandes et fournissez des informations de contexte pour les sélections effectuées dans le projet. Toutes les fonctionnalités IDE globale nécessaire pour votre VSPackage sont fournie par les services. Pour plus d’informations sur les services, consultez [Comment : obtenir un Service](../../extensibility/how-to-get-a-service.md).  
  
 Autres considérations relatives à la mise en œuvre :  
  
- Un modèle de projet unique peut contenir plusieurs types de projet.  
  
- Types de projets et les fabriques de surveillance du projet sont enregistrés indépendamment avec GUID.  
  
- Chaque projet doit avoir un fichier de modèle ou un Assistant pour initialiser le nouveau fichier de projet lorsqu’un utilisateur crée un nouveau projet via la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’interface utilisateur. Par exemple, le [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] modèles initialiser ce que deviennent des fichiers .vcproj.  
  
  L’illustration suivante montre les interfaces principales, les services et les objets qui composent une implémentation de projet standard. Vous pouvez utiliser l’Assistant application, HierUtil7, pour créer les objets sous-jacents et autres réutilisable de programmation. Pour plus d’informations sur l’application d’assistance de HierUtil7 application, consultez [pas dans la génération : à l’aide des Classes de projet HierUtil7 pour implémenter un Type de projet (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
  ![Graphique de Visual Studio projet modèle](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
  modèle de projet  
  
  Pour plus d’informations sur les interfaces et les services répertoriés dans le diagramme précédent et les autres interfaces facultatives ne pas inclus dans le diagramme, consultez [composants principaux du modèle de projet](../../extensibility/internals/project-model-core-components.md).  
  
  Projets peut prendre en charge les commandes et par conséquent doit implémenter le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface pour participer au routage des commandes via le GUID de contexte de commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Pas dans la génération : à l’aide des Classes de projet HierUtil7 pour implémenter un Type de projet (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Composants principaux du modèle projet](../../extensibility/internals/project-model-core-components.md)   
 [Création d’Instances de projet à l’aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Comment : obtenir un Service](../../extensibility/how-to-get-a-service.md)   
 [Création de types de projets](../../extensibility/internals/creating-project-types.md)

