---
title: Éléments d’un modèle de projet (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf847e35878dc84bb32fe81053c01c23e565fc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708524"
---
# <a name="elements-of-a-project-model"></a>Éléments d’un modèle de projet
Les interfaces et les implémentations de tous les projets [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] partagent une structure de base : le modèle de projet pour votre type de projet. Dans votre modèle de projet, qui est le VSPackage que vous développez, vous créez des objets qui se conforment à vos décisions de conception et de travailler en collaboration avec les fonctionnalités globales fournies par l’IDE. Bien que vous contrôlez la persistance d’un élément de projet, par exemple, vous ne contrôlez pas la notification selon laquelle un fichier doit être persistant. Lorsqu’un utilisateur met l’accent sur un élément de projet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ouvert et choisit **d’enregistrer** sur le menu De **fichier** sur la barre du menu, votre code de type de projet doit intercepter la commande à partir de l’IDE, persister le fichier et renvoyer la notification à l’IDE que le fichier n’est plus modifié.

 Votre VSPackage interagit avec l’IDE grâce à des services qui donnent accès aux interfaces IDE. Par exemple, grâce à des services particuliers, vous surveillez et acheminez les commandes et fournissez des informations contextuelles pour les sélections effectuées dans le projet. Toutes les fonctionnalités IDE mondiales nécessaires à votre VSPackage sont fournies par les services. Pour plus d’informations sur les services, voir [Comment : Obtenir un service](../../extensibility/how-to-get-a-service.md).

 Autres considérations de mise en œuvre :

- Un modèle de projet unique peut contenir plus d’un type de projet.

- Les types de projets et les usines de projet auxiliaires sont enregistrés indépendamment avec des GUID.

- Chaque projet doit disposer d’un fichier type ou d’un assistant pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] initialiser le nouveau fichier de projet lorsqu’un utilisateur crée un nouveau projet par l’intermédiaire de l’interface utilisateur. Par exemple, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] les modèles initialisent ce qui devient éventuellement des fichiers .vcproj.

  L’illustration suivante montre les interfaces primaires, les services et les objets qui composent une mise en œuvre typique du projet. Vous pouvez utiliser l’assistant d’application, `HierUtil7`, pour créer les objets sous-jacents et d’autres plaques de la chaudière de programmation. Pour plus d’informations sur l’assistant `HierUtil7` d’application, consultez les classes de [projets Use HierUtil7 pour mettre en œuvre un type de projet](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

  ![Graphique de modèle de projet de visual studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Modèle de projet

  Pour plus d’informations sur les interfaces et les services énumérés dans le diagramme précédent, et d’autres interfaces facultatives non incluses dans le diagramme, voir [les composants de base du modèle du projet](../../extensibility/internals/project-model-core-components.md).

  Les projets peuvent prendre en <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> charge les commandes et doivent donc implémenter l’interface pour participer à l’itinéraire de commande à travers le contexte de commande GUIDs.

## <a name="see-also"></a>Voir aussi
- [Liste de contrôle : Créer de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Utiliser les classes de projet HierUtil7 pour mettre en œuvre un type de projet (CMD)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Composants de base du modèle de projet](../../extensibility/internals/project-model-core-components.md)
- [Créer des instances de projet en utilisant des usines de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Comment : Obtenir un service](../../extensibility/how-to-get-a-service.md)
- [Créer des types de projets](../../extensibility/internals/creating-project-types.md)
