---
title: Création de concepteurs et éditeurs personnalisés | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c0dbc0db9d5116e372d96b43059a393ac8f4b5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105289"
---
# <a name="creating-custom-editors-and-designers"></a>Création de concepteurs et éditeurs personnalisés
L’environnement de développement intégré (IDE) Visual Studio peut héberger des différents types d’éditeur :  
  
-   L’éditeur principal de Visual Studio  
  
-   Éditeurs personnalisés  
  
-   Éditeurs externes  
  
-   Concepteurs  
  
 Les informations suivantes vous permettent de choisir le type de l’éditeur que vous avez besoin.  
  
## <a name="types-of-editor"></a>Types de l’éditeur  
 Pour plus d’informations sur l’éditeur principal de Visual Studio, consultez [étendre l’éditeur et les Services de langage](../extensibility/extending-the-editor-and-language-services.md).  
  
##### <a name="custom-editors"></a>Éditeurs personnalisés  
 Un éditeur personnalisé est celle qui est conçu pour fonctionner dans des circonstances particulières. Par exemple, vous pouvez créer un éditeur dont la fonction consiste à lire et écrire des données dans un référentiel spécifique, tel qu’un serveur Microsoft Exchange. Choisissez un éditeur personnalisé si vous souhaitez un éditeur qui fonctionne avec votre type de projet uniquement ou si vous souhaitez un éditeur qui a uniquement quelques commandes spécifiques. Notez, toutefois, que les utilisateurs ne seront pas en mesure d’utiliser un éditeur personnalisé pour modifier la norme [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projets.  
  
 Un éditeur personnalisé peut utiliser une fabrique d’éditeur et ajouter des informations sur l’Éditeur du Registre. Toutefois, le type de projet associé à l’éditeur personnalisé peut instancier l’éditeur personnalisé par d’autres moyens.  
  
 Un éditeur personnalisé permet d’effectuer l’activation sur place ou incorporation simplifié pour implémenter une vue.  
  
##### <a name="external-editors"></a>Éditeurs externes  
 Éditeurs externes sont des éditeurs qui ne sont pas intégrées dans Visual Studio, tels que Microsoft Word, le bloc-notes ou Microsoft FrontPage. Vous pouvez appeler un éditeur de ce type si, par exemple, vous sont texte en lui passant à partir de votre VSPackage. Éditeurs externes s’inscrivent elles-mêmes et peuvent être utilisés en dehors de Visual Studio. Lorsque vous appelez un éditeur externe, et qu’il peut être incorporé dans une fenêtre hôte, il apparaît dans une fenêtre dans l’IDE. Si ce n’est pas le cas, puis l’interface IDE crée une fenêtre distincte pour celle-ci.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> méthode définit la priorité du document à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> énumération. Si le `DP_External` valeur est spécifiée, le fichier peut être ouvert par un éditeur externe.  
  
## <a name="editor-design-decisions"></a>Décisions de conception de l’éditeur  
 Les questions de conception suivantes vous aideront à choisir le type de l’éditeur de meilleures adapté à votre application :  
  
-   Votre application enregistrera ses données dans des fichiers ou pas ? Si elle sera enregistré ses données dans les fichiers, sera-t-il dans un format standard ou personnalisé ?  
  
     Si vous utilisez un format de fichier standard, les autres types de projets en plus de votre projet sera capable d’ouvrir et en lecture/écriture aux données pour les. Toutefois, si vous utilisez un format de fichier personnalisé, seulement votre type de projet sera capable d’ouvrir et en lecture/écriture aux données pour les.  
  
     Si votre projet utilise des fichiers, vous devez personnaliser l’éditeur standard. Si votre projet n’utilise pas de fichiers, mais utilise à la place les éléments dans une base de données ou autre référentiel, vous devez créer un éditeur personnalisé.  
  
-   Votre éditeur n’a besoin pour héberger des contrôles ActiveX ?  
  
     Si votre éditeur héberge des contrôles ActiveX, puis implémenter un éditeur d’activation en place, comme indiqué dans [Activation en Place](../extensibility/in-place-activation.md). Si elle n’héberge pas de contrôles ActiveX, puis utiliser un éditeur d’incorporation simplifié, ou personnaliser la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur par défaut.  
  
-   Votre éditeur prend en charge plusieurs vues ? Si vous souhaitez que les vues de votre éditeur soient visibles en même temps que l’éditeur par défaut, vous devez prendre en charge plusieurs vues.  
  
     Si votre éditeur doit prendre en charge plusieurs vues, les données du document et les objets de vue de document pour l’éditeur doivent être des objets distincts. Pour plus d’informations, consultez [prenant en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md).  
  
     Si votre éditeur prend en charge plusieurs vues, vous prévoyez d’utiliser le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implémentation de mémoire tampon de texte de l’éditeur de base (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet) pour l’objet de données de document ? Autrement dit, vous souhaitez prendre en charge votre éditeur vue côte à côte avec la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal ? La possibilité de procéder est la base du Concepteur de formulaires...  
  
-   Si vous avez besoin pour héberger un éditeur externe, l’éditeur incorporable dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     S’il peut être incorporé, vous devez créer une fenêtre hôte pour l’éditeur externe et appelez ensuite la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> (méthode) et définissez la <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> valeur d’énumération pour `DP_External`. Si l’éditeur ne peut pas être incorporé, l’IDE crée automatiquement une fenêtre distincte pour celle-ci.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Procédure pas à pas : Création d’un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Explique comment créer un éditeur personnalisé.  
  
 [Procédure pas à pas : Ajout de fonctionnalités à un éditeur personnalisé](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Explique comment ajouter des fonctionnalités à un éditeur personnalisé.  
  
 [Initialisation du concepteur et configuration des métadonnées](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Explique comment initialiser un concepteur.  
  
 [Fourniture de la prise en charge de l’annulation pour les concepteurs](../extensibility/supplying-undo-support-to-designers.md)  
 Explique comment fournir la prise en charge de l’annulation pour les concepteurs.  
  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md)  
 Explique la différence entre les couleurs dans l’éditeur principal et dans les éditeurs personnalisés de syntaxe.  
  
 [Données de documents et affichage de documents dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Explique comment implémenter des données du document et les vues de document dans les éditeurs personnalisés.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Interfaces héritées dans l’éditeur](../extensibility/legacy-interfaces-in-the-editor.md)  
 Explique comment accéder à l’éditeur principal au moyen de l’API héritée.  
  
 [Développement d’un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)  
 Explique comment implémenter un service de langage.  
  
 [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explique comment créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>