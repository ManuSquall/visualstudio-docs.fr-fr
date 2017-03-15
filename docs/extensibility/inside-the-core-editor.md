---
title: "Dans l&#39;&#233;diteur de base | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - éditeur de base"
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Dans l&#39;&#233;diteur de base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'éditeur principal de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est un ensemble de plusieurs composants qui vous permettent de modifier et interroger les informations textuelles.  Si vous avez personnalisé l'éditeur principal à l'aide de l'API héritée, vous pouvez continuer à utiliser ces personnalisations, qui sont routées via des adaptateurs de l'éditeur.  Il est recommandé, cependant, que vous adaptez vos personnalisations à la nouvelle API d'éditeur.  
  
 Les zones suivantes sont certains aspects importants du éditeur principal :  
  
-   mémoire tampon de texte  
  
-   affichage de texte  
  
-   fenêtre de code  
  
-   marqueurs de texte  
  
-   Gestionnaire de texte  
  
-   Intégration avec les services de langage  
  
## Dans cette section  
 [L’instanciation de l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Fournit des instructions détaillées sur l'utilisation de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> pour créer une instance du éditeur principal.  
  
 [L'accès à la mémoire tampon de texte à l'aide de l'API héritée](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Explique le rôle de la mémoire tampon de texte dans l'éditeur principal, explique les systèmes associés qui sont utilisés pour accéder à la mémoire tampon, et fournit une liste des interfaces implémentées par l'objet de mémoire tampon de texte, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Événements de mémoire tampon de texte dans l'API héritée](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Fournit une liste des interfaces utilisées pour la notification des événements de la mémoire tampon de texte.  
  
 [Comment : s'inscrire aux événements de mémoire tampon de texte avec l'API héritée](../Topic/How%20to:%20Register%20for%20Text%20Buffer%20Events%20with%20the%20Legacy%20API.md)  
 Décrit comment informer les événements de la mémoire tampon de texte.  
  
 [Utilisation du Gestionnaire de texte pour surveiller les paramètres globaux](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Explique comment le gestionnaire de texte est utilisé pour partager des informations globales de préférence avec les principaux composants d'éditeur et comment recevoir la notification des événements de gestionnaire de texte.  
  
 [L'accès à theText vue à l'aide de l'API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Décrit le rôle de l'affichage de texte dans l'éditeur principal et répertorie les interfaces implémentées par l'objet d' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 [Personnalisation des fenêtres de Code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Fournit des informations sur la façon dont une fenêtre de code est utilisée pour placer l'affichage de texte, explique comment le gestionnaire de fenêtre de code permet de fournir des ornements à la fenêtre de code, et fournit une notification de nouvelles vues.  
  
 [Modification des paramètres d'affichage à l'aide de l'API héritée](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Fournit des instructions pas \- à \- pas sur la façon de forcer les ajustements d'affichage et explique comment supprimer les paramètres obligatoires.  
  
 [Services de langage et de l'éditeur de base](../extensibility/language-services-and-the-core-editor.md)  
 Décrit l'instanciation d'un service de langage aux ornements de code.  
  
## Rubriques connexes  
 [Procédure pas à pas : Création d'un éditeur de base et l'inscription d'un Type de fichier de l'éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Fournit des instructions pas \- à \- pas sur la façon de démarrer l'éditeur principal de code managé.  
  
 [Barre déroulante](../extensibility/drop-down-bar.md)  
 Décrit comment la barre déroulante est utilisée dans la fenêtre de code et décrit les interfaces qui sont utilisées lorsque vous implémentez une barre déroulante.  
  
 [À l'aide de marqueurs de texte avec l'API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Présente le concept des marqueurs de texte et leur utilisation dans l'éditeur principal, et répertorie les interfaces utilisées pour accéder et gérer à des marqueurs de texte.  
  
 [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md)  
 Fournit des instructions pas \- à \- pas sur la création d'un marqueur de texte et la façon d'ajouter une commande personnalisée à un menu contextuel.  
  
 [Comment : créer des marqueurs de texte personnalisé](../extensibility/how-to-create-custom-text-markers.md)  
 Fournit des instructions pas \- à \- pas sur la création d'un marqueur de texte personnalisé et de la façon de fournir le type de marqueur en tant que service.