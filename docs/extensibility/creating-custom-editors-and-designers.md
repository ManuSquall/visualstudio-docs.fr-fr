---
title: "Cr&#233;ation de concepteurs et &#233;diteurs personnalis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "concepteurs (Visual Studio SDK)"
  - "éditeurs (Visual Studio SDK), personnalisés"
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 31
---
# Cr&#233;ation de concepteurs et &#233;diteurs personnalis&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'environnement de développement intégré \(IDE\) Visual Studio peut héberger différents types d'éditeur :  
  
-   L'éditeur principal de Visual Studio  
  
-   Éditeurs personnalisés  
  
-   Éditeurs externes  
  
-   Concepteurs  
  
 Les informations suivantes vous permettent de choisir le type de l'éditeur que vous avez besoin.  
  
## Types d'éditeur  
 Pour plus d'informations sur l'éditeur principal de Visual Studio, consultez [Extension de l’éditeur et les Services de langage](../extensibility/extending-the-editor-and-language-services.md).  
  
##### Éditeurs personnalisés  
 Un éditeur personnalisé est celle qui est conçu pour fonctionner dans des circonstances particulières. Par exemple, vous pouvez créer un éditeur dont la fonction consiste à lire et écrire des données dans un référentiel spécifique, tel qu'un serveur Microsoft Exchange. Choisir un éditeur personnalisé si vous souhaitez un éditeur qui fonctionne avec votre type de projet uniquement ou si vous souhaitez un éditeur qui a uniquement quelques commandes spécifiques. Notez, cependant, que les utilisateurs ne seront pas en mesure d'utiliser un éditeur personnalisé pour modifier la norme [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projets.  
  
 Un éditeur personnalisé peut utiliser une fabrique d'éditeur et ajouter des informations sur l'Éditeur du Registre. Toutefois, le type de projet associé à l'éditeur personnalisé peut instancier l'éditeur personnalisé par d'autres moyens.  
  
 Un éditeur personnalisé permet l'activation sur place ou l'incorporation simplifié pour implémenter une vue.  
  
##### Éditeurs externes  
 Éditeurs externes sont des éditeurs qui ne sont pas intégrés à Visual Studio, telles que Microsoft Word, le bloc\-notes ou Microsoft FrontPage. Vous pouvez appeler un éditeur de ce type si, par exemple, vous sont texte en lui passant à partir de votre VSPackage. Éditeurs externes s'inscrire eux\-mêmes et peuvent être utilisés en dehors de Visual Studio. Lorsque vous appelez un éditeur externe, et qu'il peut être incorporé dans une fenêtre hôte, elle apparaît dans une fenêtre de l'IDE. Dans le cas contraire, l'IDE crée ensuite une fenêtre distincte pour elle.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> méthode définit la priorité du document à l'aide de la <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> \(énumération\). Si la `DP_External` est spécifiée, le fichier peut être ouvert par un éditeur externe.  
  
## Décisions de conception de l'éditeur  
 Les questions de conception suivantes vous aideront à choisir le type de l'éditeur de meilleures adapté à votre application :  
  
-   Votre application enregistrera ses données dans des fichiers ou pas ? Si elle sera enregistré ses données dans des fichiers, ils seront dans un format standard ou personnalisé ?  
  
     Si vous utilisez un format de fichier standard, les autres types de projets en plus de votre projet sera capable d'ouvrir et de données en lecture\/écriture pour les. Toutefois, si vous utilisez un format de fichier personnalisé, votre type de projet seulement sera capable d'ouvrir et de données en lecture\/écriture pour les.  
  
     Si votre projet utilise des fichiers, vous devez personnaliser l'éditeur standard. Si votre projet n'utilise pas de fichiers, mais utilise plutôt des éléments dans une base de données ou tout autre référentiel, vous devez créer un éditeur personnalisé.  
  
-   Votre éditeur n'a besoin pour héberger des contrôles ActiveX ?  
  
     Si votre éditeur héberge des contrôles ActiveX, puis implémentez un éditeur d'activation sur place, comme indiqué dans [activation sur place](../misc/in-place-activation.md). Si elle n'héberge pas de contrôles ActiveX, puis utilisez un éditeur d'incorporation simplifié ou personnaliser la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur par défaut.  
  
-   Votre éditeur prend en charge plusieurs vues ? Si vous souhaitez que les vues de votre éditeur soient visibles en même temps que l'éditeur par défaut, vous devez prendre en charge plusieurs vues.  
  
     Si votre éditeur doit prendre en charge plusieurs vues, les données de documents et les objets de vue de document de l'éditeur doivent être des objets distincts. Pour plus d'informations, consultez [Prend en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md).  
  
     Si votre éditeur prend en charge plusieurs vues, prévoyez\-vous d'utiliser le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implémentation de mémoire tampon de texte de l'éditeur de base \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet\) pour l'objet de données de document ? Autrement dit, vous souhaiteriez prendre en charge votre éditeur vue côté à côte avec la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal ? La possibilité de procéder est la base du Concepteur de formulaires...  
  
-   Si vous avez besoin d'héberger un éditeur externe, il peut l'éditeur être incorporé dans les [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     S'il peut être incorporé, vous devez créer une fenêtre hôte de l'éditeur externe et appelez ensuite la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> méthode et affectez le <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> valeur d'énumération `DP_External`. Si l'éditeur ne peut pas être incorporé, l'IDE crée automatiquement une fenêtre distincte pour celui\-ci.  
  
## Dans cette section  
 [Procédure pas à pas : Création d'un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Explique comment créer un éditeur personnalisé.  
  
 [Procédure pas à pas : Ajout de fonctionnalités à un éditeur personnalisé](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Explique comment ajouter des fonctionnalités à un éditeur personnalisé.  
  
 [L'initialisation du concepteur et la Configuration des métadonnées](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Explique comment initialiser un concepteur.  
  
 [Fournissant la prise en charge de l'annulation pour les concepteurs](../extensibility/supplying-undo-support-to-designers.md)  
 Explique comment fournir la prise en charge de l'annulation pour les concepteurs.  
  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md)  
 Explique la différence entre les couleurs dans l'éditeur principal et dans les éditeurs personnalisés de la syntaxe.  
  
 [Données de documents et affichage de documents dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Explique comment implémenter des données de documents et vues de document dans les éditeurs personnalisés.  
  
## Rubriques connexes  
 [Interfaces héritées dans l’éditeur](../extensibility/legacy-interfaces-in-the-editor.md)  
 Explique comment accéder à l'éditeur principal au moyen de l'API héritée.  
  
 [Développement d'un Service de langage](../extensibility/internals/developing-a-legacy-language-service.md)  
 Explique comment implémenter un service de langage.  
  
 [Extension des autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explique comment créer des éléments d'interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>