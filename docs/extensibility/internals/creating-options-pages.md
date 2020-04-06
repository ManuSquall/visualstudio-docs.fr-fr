---
title: Création de pages Options (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 368efaa78a56723d4a72c482bea9ee739385127e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709154"
---
# <a name="create-options-pages"></a>Créer des pages d’options
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le cadre de paquet <xref:Microsoft.VisualStudio.Shell.DialogPage> géré, les classes dérivées de l’extension de l’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en ajoutant des pages **Options** sous le menu **Tools.**

 Un objet implémentant une page **d’option Outils** <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> donnés est associé à des VSPackages spécifiques par l’objet.

 Parce que l’environnement instantané l’objet implémentant une page **d’options d’outils** particulières lorsque cette page particulière est affichée par l’IDE:

- Une page **d’option outils** doit être implémentée sur son propre objet, et non sur l’objet implémentant un VSPackage.

- Un objet ne peut pas implémenter plusieurs pages **d’options d’outils.**

## <a name="register-as-a-tools-options-page-provider"></a>Inscrivez-vous en tant que fournisseur de pages Options d’outils
 Une configuration utilisateur de support VSPackage via les pages **Tools Options** indique les objets fournissant ces pages **d’options d’outils** en appliquant des instances d’application <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à la <xref:Microsoft.VisualStudio.Shell.Package> mise en œuvre.

 Il doit y <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> avoir <xref:Microsoft.VisualStudio.Shell.DialogPage>un exemple de chaque type dérivé qui implémente une page **Options d’outils.**

 Chaque instance <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> utilise le type qui implémente la page **Options outils,** les chaînes qui contiennent la catégorie et la sous-catégorie utilisées pour identifier une page **Options d’outils,** et les informations sur les ressources pour enregistrer le type comme fournissant une page **Options d’outils.**

## <a name="persist-tools-options-page-state"></a>État de la page Options d’outils persistants
 Si la mise en œuvre d’une page **Options d’outils** est enregistrée avec le support d’automatisation activé, l’IDE persiste l’état de la page ainsi que toutes les autres pages **Options d’outils.**

 Un VSPackage peut gérer sa <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>propre persistance en utilisant . Une seule ou l’autre méthode de persistance doit être utilisée.

## <a name="implement-dialogpage-class"></a>Mettre en œuvre la classe DialogPage
 Un objet fournissant la mise en <xref:Microsoft.VisualStudio.Shell.DialogPage>œuvre d’un type dérivé d’un VSPackage peut tirer parti des caractéristiques héritées suivantes :

- Une fenêtre d’interface utilisateur par défaut.

- Un mécanisme de persistance <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> par défaut disponible soit <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> s’il `true` est <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> appliqué à la classe, soit si la propriété est réglée pour le qui est appliqué à la classe.

- Soutien à l’automatisation.

  L’exigence minimale pour un objet implémentant une page **Options d’outils** à l’aide <xref:Microsoft.VisualStudio.Shell.DialogPage> est l’ajout de propriétés publiques.

  Si la classe s’est correctement enregistrée en tant que fournisseur de pages **Options d’outils,** ses propriétés publiques sont disponibles sur la section **Options** du menu **Tools** sous la forme d’une grille de propriété.

  Toutes ces fonctionnalités par défaut peuvent être remplacées. Par exemple, pour créer une interface utilisateur plus sophistiquée, <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>il suffit de ne dépasser que la mise en œuvre par défaut de .

## <a name="example"></a>Exemple
 Ce qui suit est une simple mise en œuvre "Bonjour monde" d’une page d’options. L’ajout du code suivant à un projet par défaut créé par le modèle de paquet Visual Studio avec l’option **De commande de menu** sélectionnée démontrera adéquatement la fonctionnalité de la page d’option.

### <a name="description"></a>Description
 La classe suivante définit une page d’options minimale "Hello world". Lorsqu’il est ouvert, `HelloWorld` l’utilisateur peut définir la propriété publique dans une grille de propriété.

### <a name="code"></a>Code
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Description
 L’application de l’attribut suivant à la classe de paquet rend la page d’options disponible lorsque le paquet se charge. Les numéros sont des Œd de ressources arbitraires pour la catégorie et la page, et la valeur Boolean à la fin précise si la page prend en charge l’automatisation.

### <a name="code"></a>Code
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Description
 Le gestionnaire d’événements suivant affiche un résultat en fonction de la valeur de la propriété définie dans la page d’options. Il utilise <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> la méthode avec le résultat explicitement jeté dans le type de page d’option personnalisée pour accéder aux propriétés exposées par la page.

 Dans le cas d’un projet généré par le `MenuItemCallback` modèle de paquet, appelez cette fonction de la fonction pour l’attacher à la commande par défaut ajoutée au menu **Tools.**

### <a name="code"></a>Code
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Voir aussi
- [Étendre les paramètres et les options de l’utilisateur](../../extensibility/extending-user-settings-and-options.md)
- [Support d’automatisation pour les pages d’options](../../extensibility/internals/automation-support-for-options-pages.md)
