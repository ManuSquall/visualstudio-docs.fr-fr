---
title: Éléments d’un modèle de projet | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708524"
---
# <a name="elements-of-a-project-model"></a>Éléments d’un modèle de projet
Les interfaces et les implémentations de tous les projets dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] partagent une structure de base : le modèle de projet pour votre type de projet. Dans votre modèle de projet, qui est le VSPackage que vous développez, vous créez des objets conformes à vos décisions de conception et travaillez conjointement avec les fonctionnalités globales fournies par l’IDE. Même si vous contrôlez la façon dont un élément de projet est rendu persistant, par exemple, vous ne contrôlez pas la notification qu’un fichier doit être rendu persistant. Lorsqu’un utilisateur place le focus sur un élément de projet ouvert et choisit **Enregistrer** dans le menu **fichier** de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barre de menus, votre code de type de projet doit intercepter la commande de l’IDE, conserver le fichier et renvoyer la notification à l’IDE pour que le fichier ne soit plus modifié.

 Votre VSPackage interagit avec l’IDE via des services qui fournissent l’accès aux interfaces IDE. Par exemple, par le biais de services particuliers, vous surveillez et Routez les commandes et fournissez des informations de contexte pour les sélections effectuées dans le projet. Toutes les fonctionnalités globales de l’IDE nécessaires à votre VSPackage sont fournies par les services. Pour plus d’informations sur les services, consultez [Comment : obtenir un service](../../extensibility/how-to-get-a-service.md).

 Autres considérations relatives à l’implémentation :

- Un modèle de projet unique peut contenir plusieurs types de projets.

- Les types de projets et les fabriques de projet de surveillance sont enregistrés indépendamment avec les GUID.

- Chaque projet doit avoir un fichier de modèle ou un Assistant pour initialiser le nouveau fichier projet lorsqu’un utilisateur crée un nouveau projet par le biais de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface utilisateur. Par exemple, les [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modèles initialisent ce qui finit par devenir des fichiers. vcproj.

  L’illustration suivante montre les interfaces, les services et les objets principaux qui composent une implémentation de projet typique. Vous pouvez utiliser l’application auxiliaire, `HierUtil7` , pour créer les objets sous-jacents et d’autres programmations réutilisables. Pour plus d’informations sur l' `HierUtil7` application d’assistance, consultez [utiliser des classes de projet HierUtil7 pour implémenter un type de projet (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

  ![Graphique du modèle de projet Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Modèle de projet

  Pour plus d’informations sur les interfaces et les services répertoriés dans le diagramme précédent, ainsi que sur les autres interfaces facultatives non incluses dans le diagramme, consultez [composants de base du modèle de projet](../../extensibility/internals/project-model-core-components.md).

  Les projets peuvent prendre en charge les commandes et, par conséquent, doivent implémenter l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface pour participer au routage des commandes via les GUID de contexte de commande.

## <a name="see-also"></a>Voir aussi
- [Liste de vérification : créer des types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Utiliser des classes de projet HierUtil7 pour implémenter un type de projet (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Composants de base du modèle de projet](../../extensibility/internals/project-model-core-components.md)
- [Créer des instances de projet à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Comment : obtenir un service](../../extensibility/how-to-get-a-service.md)
- [Créer des types de projet](../../extensibility/internals/creating-project-types.md)
