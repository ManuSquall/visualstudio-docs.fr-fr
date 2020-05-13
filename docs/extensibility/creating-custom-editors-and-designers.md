---
title: Création d’éditeurs et de designers personnalisés Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9f56b82225e1e40782b6753bea03d3c1780f596
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739473"
---
# <a name="create-custom-editors-and-designers"></a>Créez des éditeurs et des designers personnalisés

L’environnement de développement intégré Visual Studio (IDE) peut accueillir différents types d’éditeurs :

- L’éditeur de base de Visual Studio

- Éditeurs personnalisés

- Rédacteurs externes

- Concepteurs

Les informations suivantes vous aident à choisir le type d’éditeur dont vous avez besoin.

## <a name="types-of-editor"></a>Types d’éditeurs

Pour plus d’informations sur l’éditeur de base Visual Studio, voir [Extend the editor and language services](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Éditeurs personnalisés
 Un éditeur personnalisé est celui qui est conçu pour travailler dans des circonstances spécialisées. Par exemple, vous pouvez créer un éditeur dont la fonction est de lire et d’écrire des données à un référentiel spécifique, comme un serveur Microsoft Exchange. Choisissez un éditeur personnalisé si vous voulez un éditeur qui fonctionne avec votre type de projet seulement ou si vous voulez un éditeur qui n’a que quelques commandes spécifiques. Notez toutefois que les utilisateurs ne pourront pas utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un éditeur personnalisé pour modifier des projets standard.

 Un éditeur personnalisé peut utiliser une usine d’éditeur et ajouter des informations sur l’éditeur au registre. Cependant, le type de projet associé à l’éditeur personnalisé peut instantanée l’éditeur personnalisé d’autres façons.

 Un éditeur personnalisé peut utiliser soit l’activation sur place, soit l’intégration simplifiée pour implémenter une vue.

### <a name="external-editors"></a>Rédacteurs externes
 Les éditeurs externes sont des éditeurs qui ne sont pas intégrés dans Visual Studio, tels que Microsoft Word, Notepad, ou Microsoft FrontPage. Vous pouvez appeler un tel éditeur si, par exemple, vous lui transmettez du texte à partir de votre VSPackage. Les éditeurs externes s’enregistrent et peuvent être utilisés en dehors de Visual Studio. Lorsque vous appelez un éditeur externe, et il peut être intégré dans une fenêtre d’hôte, puis il apparaît dans une fenêtre de l’IDE. Si ce n’est pas le cas, alors l’IDE crée une fenêtre séparée pour elle.

 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> méthode définit la priorité <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> du document en utilisant l’énumération. Si `DP_External` la valeur est spécifiée, le fichier peut être ouvert par un éditeur externe.

## <a name="editor-design-decisions"></a>Décisions de conception de l’éditeur
 Les questions de conception suivantes vous aideront à choisir le type d’éditeur le mieux adapté à votre application :

- Votre application enregistrera-t-elle ses données dans des fichiers ou non ? S’il enregistre ses données dans les fichiers, seront-ils dans un format personnalisé ou standard?

   Si vous utilisez un format de fichier standard, d’autres types de projets en plus de votre projet pourront leur ouvrir et lire/écrire des données. Toutefois, si vous utilisez un format de fichier personnalisé, seul votre type de projet sera en mesure d’ouvrir et de lire/écrire des données.

   Si votre projet utilise des fichiers, vous devez personnaliser l’éditeur standard. Si votre projet n’utilise pas de fichiers, mais utilise plutôt des éléments dans une base de données ou un autre référentiel, alors vous devez créer un éditeur personnalisé.

- Votre éditeur doit-il héberger les contrôles ActiveX ?

   Si votre éditeur héberge les commandes ActiveX, implémentez un éditeur d’activation sur place, tel qu’indiqué dans [l’activation](/visualstudio/misc/in-place-activation?view=vs-2015)place . S’il n’héberge pas les commandes ActiveX, utilisez un éditeur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] d’intégration simplifié ou personnalisez l’éditeur par défaut.

- Votre rédacteur en chef soutiendra-t-il plusieurs points de vue ? Vous devez prendre en charge plusieurs vues si vous voulez que les vues de votre éditeur soient visibles en même temps que l’éditeur par défaut.

   Si votre éditeur doit prendre en charge plusieurs vues, les données de document et les objets de vue de document pour l’éditeur doivent être des objets distincts. Pour plus d’informations, voir [Support plusieurs vues de documents](../extensibility/supporting-multiple-document-views.md).

   Si votre éditeur prend en charge plusieurs [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vues, prévoyez-vous<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> d’utiliser la mise en œuvre de mémoire texte (objet) de l’éditeur de base pour votre objet de données de document ? Autrement dit, voulez-vous soutenir votre point de vue [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur côte à côte avec l’éditeur de base? La capacité de le faire est la base du concepteur de formulaires.

- Si vous avez besoin d’héberger un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]éditeur externe, l’éditeur peut-il être intégré à l’intérieur ?

   Si elle peut être intégrée, vous devez créer une fenêtre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> d’hôte <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> pour l’éditeur externe, puis appeler la méthode et définir la valeur de recensement à `DP_External`. Si l’éditeur ne peut pas être intégré, l’IDE créera automatiquement une fenêtre séparée pour elle.

## <a name="in-this-section"></a>Dans cette section

[Procédure pas à pas : Créez un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md)\
Explique comment créer un éditeur personnalisé.

[Procédure pas à pas : Ajoutez des fonctionnalités à un éditeur personnalisé](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Explique comment ajouter des fonctionnalités à un éditeur personnalisé.

[Initialisation et configuration de métadonnées de concepteur](../extensibility/designer-initialization-and-metadata-configuration.md)\
Explique comment initialiser un designer.

[Fournir un soutien annuler aux concepteurs](../extensibility/supplying-undo-support-to-designers.md)\
Explique comment fournir un soutien annuler pour les concepteurs.

[Coloriage Syntax dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md)\
Explique la différence entre la coloration syntaxe dans l’éditeur de base et dans les éditeurs personnalisés.

[Données documentaires et vue de documents dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Explique comment implémenter les données de documents et documenter les vues dans les éditeurs personnalisés.

## <a name="related-sections"></a>Sections connexes

[Interfaces héritées dans l’éditeur](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
Explique comment accéder à l’éditeur de base au moyen de l’API hérité.

[Développer un service linguistique hérité](../extensibility/internals/developing-a-legacy-language-service.md)\
Explique comment mettre en œuvre un service linguistique.

[Étendre d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Explique comment créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
