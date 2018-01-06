---
title: "À l’intérieur de l’éditeur principal | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e4612f5779d6177d58cef7f087ef6e11bbe4ebd9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="inside-the-core-editor"></a>Dans l’éditeur de base
Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal est un ensemble de plusieurs composants qui vous permettent de modifier et d’interroger les informations textuelles. Si vous avez personnalisé l’éditeur principal à l’aide de l’API héritée, vous pouvez continuer à utiliser ces personnalisations, ce qui seront routées via des cartes de l’éditeur. Il est recommandé, toutefois, que vous adapter les personnalisations de l’API de l’éditeur de nouveau.  
  
 Les domaines suivants sont des aspects importants de l’éditeur principal :  
  
-   Mémoire tampon de texte  
  
-   Affichage de texte  
  
-   Fenêtre Code  
  
-   Marqueurs de texte  
  
-   Gestionnaire de texte  
  
-   Intégration avec les services de langage  
  
## <a name="in-this-section"></a>Dans cette section  
 [L’instanciation de l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Fournit des instructions détaillées sur l’utilisation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> pour créer une instance de la base de l’éditeur.  
  
 [L’accès à la mémoire tampon de texte à l’aide de l’API héritée](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Décrit le rôle de la mémoire tampon de texte dans l’éditeur principal, explique les systèmes associés qui sont utilisés pour accéder à la mémoire tampon et fournit une liste des interfaces implémentées par l’objet de mémoire tampon de texte, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Événements de mémoire tampon de texte dans l’API hérité](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Fournit une liste des interfaces qui sont utilisées pour la notification d’événements de mémoire tampon de texte.  
  
 [Comment : s’inscrire aux événements de mémoire tampon de texte avec l’API hérité](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Décrit comment informer des événements de mémoire tampon de texte.  
  
 [À l’aide du Gestionnaire de texte pour surveiller des paramètres globaux](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Explique comment le Gestionnaire de texte est utilisé pour partager des informations de préférences global avec les principaux composants de l’éditeur et recevoir une notification d’événements du Gestionnaire de texte.  
  
 [L’accès à theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Décrit le rôle de l’affichage texte dans l’éditeur principal et répertorie les interfaces implémentées par le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objet.  
  
 [Personnalisation des fenêtres de Code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Fournit des informations sur comment une fenêtre de code est utilisée pour placer l’affichage de texte, explique comment le Gestionnaire de fenêtre de code permet de fournir des ornements à la fenêtre de code et fournit une notification de nouveaux affichages.  
  
 [Modification des paramètres de la vue à l’aide de l’API héritée](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Fournit des instructions étape par étape comment forcer les paramètres d’affichage et la suppression forcée des paramètres.  
  
 [Services de langage et de l’éditeur principal](../extensibility/language-services-and-the-core-editor.md)  
 Décrit l’instanciation d’un service de langage pour les décorations de code de contrôle.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Procédure pas à pas : Création d’un éditeur de base et l’inscription d’un Type de fichier de l’éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Fournit des instructions détaillées sur la façon de démarrer l’éditeur principal à partir du code managé.  
  
 [Barre déroulante](../extensibility/drop-down-bar.md)  
 Explique comment la barre déroulante est utilisée dans la fenêtre de code et décrit les interfaces qui sont utilisées lorsque vous implémentez une barre de menu déroulant.  
  
 [À l’aide de marqueurs de texte avec l’API hérité](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Explique le concept des marqueurs de texte et comment elles sont utilisées dans l’éditeur principal et répertorie les interfaces qui sont utilisées pour accéder et de gérer des marqueurs de texte.  
  
 [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md)  
 Fournit des instructions détaillées sur la création d’un marqueur de texte et comment ajouter une commande personnalisée à un menu contextuel.  
  
 [Comment : créer des marqueurs de texte personnalisé](../extensibility/how-to-create-custom-text-markers.md)  
 Fournit des instructions détaillées sur la création d’un marqueur de texte personnalisé et comment fournir le type de marqueur en tant que service.