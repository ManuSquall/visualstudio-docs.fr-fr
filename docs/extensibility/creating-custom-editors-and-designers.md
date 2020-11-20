---
title: Création d’éditeurs et de concepteurs personnalisés | Microsoft Docs
description: 'Découvrez les différents types d’éditeurs qui peuvent être hébergés par l’IDE de Visual Studio : l’éditeur principal, les éditeurs personnalisés, les éditeurs externes et les concepteurs.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9dd2d3923776cc0666a3efd12a32fc9e4e8735a0
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94973609"
---
# <a name="create-custom-editors-and-designers"></a>Créer des éditeurs et des concepteurs personnalisés

L’environnement de développement intégré (IDE) de Visual Studio peut héberger différents types d’éditeur :

- Éditeur de base de Visual Studio

- Éditeurs personnalisés

- Éditeurs externes

- Concepteurs

Les informations suivantes vous aideront à choisir le type d’éditeur dont vous avez besoin.

## <a name="types-of-editor"></a>Types d’éditeur

Pour plus d’informations sur l’éditeur principal de Visual Studio, consultez [étendre l’éditeur et les services de langage](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Éditeurs personnalisés
 Un éditeur personnalisé est un éditeur conçu pour fonctionner dans des circonstances particulières. Par exemple, vous pouvez créer un éditeur dont la fonction consiste à lire et à écrire des données dans un référentiel spécifique, tel qu’un serveur Microsoft Exchange. Choisissez un éditeur personnalisé si vous souhaitez un éditeur qui fonctionne avec votre type de projet uniquement ou si vous souhaitez un éditeur qui ne contient que quelques commandes spécifiques. Notez, toutefois, que les utilisateurs ne seront pas en mesure d’utiliser un éditeur personnalisé pour modifier les [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projets standard.

 Un éditeur personnalisé peut utiliser une fabrique d’éditeur et ajouter des informations sur l’éditeur au registre. Toutefois, le type de projet associé à l’éditeur personnalisé peut instancier l’éditeur personnalisé d’une autre manière.

 Un éditeur personnalisé peut utiliser l’activation sur place ou l’incorporation simplifiée pour implémenter une vue.

### <a name="external-editors"></a>Éditeurs externes
 Les éditeurs externes sont des éditeurs qui ne sont pas intégrés à Visual Studio, tels que Microsoft Word, le bloc-notes ou Microsoft FrontPage. Vous pouvez appeler un tel éditeur si, par exemple, vous transmettez du texte à partir de votre VSPackage. Les éditeurs externes s’inscrivent eux-mêmes et peuvent être utilisés en dehors de Visual Studio. Lorsque vous appelez un éditeur externe et qu’il peut être incorporé dans une fenêtre hôte, il apparaît dans une fenêtre de l’IDE. Si ce n’est pas le cas, l’IDE crée une fenêtre distincte pour celui-ci.

 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> méthode définit la priorité du document à l’aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> énumération. Si la `DP_External` valeur est spécifiée, le fichier peut être ouvert par un éditeur externe.

## <a name="editor-design-decisions"></a>Décisions de conception de l’éditeur
 Les questions de conception suivantes vous aideront à choisir le type d’éditeur le mieux adapté à votre application :

- Votre application va-t-elle enregistrer ses données dans les fichiers ? S’il enregistrera ses données dans des fichiers, sera-t-il dans un format personnalisé ou standard ?

   Si vous utilisez un format de fichier standard, d’autres types de projets, en plus de votre projet, pourront ouvrir et lire/écrire des données. Toutefois, si vous utilisez un format de fichier personnalisé, seul votre type de projet pourra ouvrir et lire/écrire des données sur ces derniers.

   Si votre projet utilise des fichiers, vous devez personnaliser l’éditeur standard. Si votre projet n’utilise pas de fichiers, mais utilise plutôt des éléments d’une base de données ou d’un autre référentiel, vous devez créer un éditeur personnalisé.

- Votre éditeur a-t-il besoin d’héberger des contrôles ActiveX ?

   Si votre éditeur héberge des contrôles ActiveX, implémentez un éditeur d’activation sur place, comme indiqué dans [activation sur place](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015). S’il n’héberge pas de contrôles ActiveX, utilisez un éditeur d’incorporation simplifié ou personnalisez l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur par défaut.

- Votre éditeur prendra-t-il en charge plusieurs vues ? Vous devez prendre en charge plusieurs vues Si vous souhaitez que les affichages de votre éditeur soient visibles en même temps que l’éditeur par défaut.

   Si votre éditeur doit prendre en charge plusieurs vues, les données de document et les objets de vue de document de l’éditeur doivent être des objets distincts. Pour plus d’informations, consultez [prendre en charge plusieurs vues de documents](../extensibility/supporting-multiple-document-views.md).

   Si votre éditeur prend en charge plusieurs vues, prévoyez-vous d’utiliser l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implémentation de mémoire tampon de texte de l’éditeur principal ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet) pour votre objet de données de document ? Autrement dit, voulez-vous prendre en charge la vue de l’éditeur côte à côte avec l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal ? La capacité à effectuer cette opération est la base du concepteur de formulaires.

- Si vous devez héberger un éditeur externe, peut-il être incorporé dans l’éditeur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ?

   S’il peut être incorporé, vous devez créer une fenêtre hôte pour l’éditeur externe, puis appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> méthode et définir la <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> valeur d’énumération sur `DP_External` . Si l’éditeur ne peut pas être incorporé, l’IDE crée automatiquement une fenêtre distincte pour celui-ci.

## <a name="in-this-section"></a>Dans cette section

[Procédure pas à pas : création d’un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md)\
Explique comment créer un éditeur personnalisé.

[Procédure pas à pas : ajouter des fonctionnalités à un éditeur personnalisé](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Explique comment ajouter des fonctionnalités à un éditeur personnalisé.

[Initialisation du concepteur et configuration des métadonnées](../extensibility/designer-initialization-and-metadata-configuration.md)\
Explique comment initialiser un concepteur.

[Fournir une prise en charge de l’annulation aux concepteurs](../extensibility/supplying-undo-support-to-designers.md)\
Explique comment fournir une prise en charge de l’annulation pour les concepteurs.

[Coloration de la syntaxe dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md)\
Explique la différence entre la coloration de la syntaxe dans l’éditeur principal et dans les éditeurs personnalisés.

[Données de document et vue de document dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Explique comment implémenter des données de document et des vues de document dans des éditeurs personnalisés.

## <a name="related-sections"></a>Sections connexes

[Interfaces héritées dans l’éditeur](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)\
Explique comment accéder à l’éditeur principal au moyen de l’API héritée.

[Développer un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)\
Explique comment implémenter un service de langage.

[Étendre d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Explique comment créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
