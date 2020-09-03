---
title: Extension des propriétés | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7064128c54434b0a7bb8799e62b751e765511c48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708420"
---
# <a name="extend-properties"></a>Étendre les propriétés
La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fenêtre **Propriétés** est un Explorateur de propriétés universel pour les composants COM et com+ et prend en charge tous les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] produits. La fenêtre **Propriétés** fonctionne avec les `ITypeInfo` informations de type et les métadonnées com+ pour répertorier les propriétés au moment du design de l’objet actuellement sélectionné dans toute autre fenêtre de l’environnement de développement intégré (IDE).

 La fenêtre **Propriétés** , qui peut être ouverte en appuyant sur **F4** sur le clavier, ou en sélectionnant **fenêtre Propriétés** dans le menu **affichage** , permet d’afficher et de modifier les propriétés et événements de conception indépendants, au moment du design et les objets sélectionnés. Les propriétés dépendantes de la configuration, associées aux solutions et aux projets, sont affichées dans les [pages de propriétés](../../extensibility/internals/property-pages.md). Pour plus d’informations, [Gérez les options de configuration](../../extensibility/internals/managing-configuration-options.md).

 ![Présentation de fenêtre Propriétés](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") Fenêtre Propriétés

 Cette section fournit des informations détaillées relatives aux zones individuelles de la fenêtre **Propriétés** et aux interfaces que vous devez implémenter et appeler pour remplir la fenêtre.

## <a name="in-this-section"></a>Contenu de cette section
- [Présentation de Fenêtre Propriétés](../../extensibility/internals/properties-window-overview.md)

 Explique l’objectif de la fenêtre **Propriétés** par rapport à la fenêtre outil et à la fenêtre de document.

- [Stratégie de modèle et le Fenêtre Propriétés](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Explique comment un projet est contenu dans un projet de modèle d’entreprise et comment ce projet de modèle d’entreprise peut appliquer la stratégie.

- [Fenêtre Propriétés les champs et les interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Décrit la base de la sélection qui détermine les informations qui s’affichent dans la fenêtre **Propriétés** .

- [Liste d’objets Fenêtre Propriétés](../../extensibility/internals/properties-window-object-list.md)

 Décrit l’objectif de la liste d’objets de la fenêtre **Propriétés** , décrivant comment, lorsqu’un autre objet de cette liste déclenche un appel, l’environnement est informé qu’un nouvel objet a été sélectionné.

- [Boutons Fenêtre Propriétés](../../extensibility/internals/properties-window-buttons.md)

 Explique l’objectif des quatre boutons par défaut affichés dans la barre d’outils de la fenêtre **Propriétés** .

- [Grille d’affichage des propriétés](../../extensibility/internals/properties-display-grid.md)

 Explique où se trouvent les champs des noms de propriétés et des valeurs de propriété dans la grille.

## <a name="related-sections"></a>Sections connexes
- [Types de projets](../../extensibility/internals/project-types.md)

 Décrit les projets comme des blocs de construction de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Compiler et générer](../../ide/compiling-and-building-in-visual-studio.md)

 Décrit comment vous pouvez utiliser la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plateforme pour tester et déboguer des applications en continu au fur et à mesure de leur génération.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Décrit l' `IDispatch` interface, qui a été conçue pour prendre en charge l’automatisation, en fournissant un mécanisme de liaison tardive permettant d’accéder à des informations sur les méthodes et les propriétés d’un objet et de les récupérer.

- [Gérer les paramètres d’application (.NET)](../../ide/managing-application-settings-dotnet.md)

 Fournit une vue d’ensemble des paramètres d’application qui vous permettent de configurer votre application afin que les valeurs de propriété soient stockées dans un fichier de configuration externe plutôt que dans le code compilé de l’application.

- [Solutions et projets](../../ide/solutions-and-projects-in-visual-studio.md)

 Explique comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gère efficacement les éléments tels que les références, les connexions de données, les dossiers et les fichiers requis par votre effort de développement via des solutions et des projets.

- [Étendre d’autres parties de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Explique comment utiliser les services de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
