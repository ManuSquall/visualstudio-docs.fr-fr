---
title: Éléments d’un modèle de projet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 4933e73df93c1f8a3bcf62e03b6883c0096f1d8f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135557"
---
# <a name="elements-of-a-project-model"></a>Éléments d’un modèle de projet
Les interfaces et les implémentations de tous les projets de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] partagent une structure de base : le modèle de projet pour votre type de projet. Dans votre modèle de projet, qui est le VSPackage que vous développez, vous créez des objets conformes à vos décisions de conception et de travail ainsi que les fonctionnalités globales fournies par l’IDE. Bien que vous contrôlez la façon dont un élément de projet est persistant, par exemple, vous ne contrôlez pas notification qu’un fichier doit être persistante. Lorsqu’un utilisateur place le focus sur un élément de projet ouvert et choisit **enregistrer** sur la **fichier** menu sur le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu barre, votre code de type de projet doit intercepter la commande à partir de l’IDE, conserver le fichier, et envoyer la notification à l’IDE que le fichier est n’est plus modifié.  
  
 Votre VSPackage interagit avec l’IDE via les services qui fournissent l’accès aux interfaces IDE. Par exemple, par le biais des services particuliers, vous analyse et routage des commandes et fournissez des informations de contexte pour les sélections effectuées dans le projet. Toutes les fonctionnalités IDE globale nécessaire pour votre VSPackage sont fournie par les services. Pour plus d’informations sur les services, consultez [Comment : obtenir un Service](../../extensibility/how-to-get-a-service.md).  
  
 Autres considérations relatives à la mise en œuvre :  
  
-   Un modèle de projet unique peut contenir plusieurs types de projet.  
  
-   Types de projets et les fabriques de surveillance du projet sont enregistrés indépendamment des GUID.  
  
-   Chaque projet doit avoir un fichier de modèle ou un Assistant pour initialiser le nouveau fichier de projet lorsqu’un utilisateur crée un nouveau projet via la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur. Par exemple, le [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modèles initialiser ce que deviennent les fichiers .vcproj.  
  
 L’illustration suivante montre les interfaces principales, les services et les objets qui composent une implémentation d’un projet standard. Vous pouvez utiliser l’Assistant application, HierUtil7, pour créer les objets sous-jacents et les autres réutilisable de programmation. Pour plus d’informations sur l’application d’assistance de HierUtil7 application, consultez [pas dans la Build : utilisation de Classes de projet HierUtil7 pour implémenter un Type de projet (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
 ![Graphique de Visual Studio projet modèle](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
modèle de projet  
  
 Pour plus d’informations sur les interfaces et les services répertoriés dans le diagramme précédent et les autres interfaces facultatives ne pas inclus dans le diagramme, consultez [composants principaux du modèle de projet](../../extensibility/internals/project-model-core-components.md).  
  
 Projets peut prendre en charge les commandes et par conséquent doit implémenter la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface pour participer au routage des commandes via le contexte de la commande GUID.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Pas dans la génération : à l’aide des Classes de projet HierUtil7 pour implémenter un Type de projet (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Composants de modèle de projet](../../extensibility/internals/project-model-core-components.md)   
 [Création d’Instances de projet à l’aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Comment : obtenir un Service](../../extensibility/how-to-get-a-service.md)   
 [Création de types de projets](../../extensibility/internals/creating-project-types.md)