---
title: À l’intérieur de l’éditeur principal | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf9bc42aec3aac5acc996487f99c7e1f29ca252c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203950"
---
# <a name="inside-the-core-editor"></a>À l’intérieur de l’éditeur de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur principal est un ensemble de plusieurs composants qui vous permettent de modifier et d’interroger des informations textuelles. Si vous avez personnalisé l’éditeur principal à l’aide de l’API héritée, vous pouvez continuer à utiliser ces personnalisations, qui seront acheminées via les adaptateurs de l’éditeur. Toutefois, il est recommandé d’adapter vos personnalisations à la nouvelle API de l’éditeur.  
  
 Les aspects importants de l’éditeur principal sont les suivants :  
  
- Mémoire tampon de texte  
  
- Affichage de texte  
  
- Fenêtre de code  
  
- Marqueurs de texte  
  
- Gestionnaire de texte  
  
- Intégration aux services de langage  
  
## <a name="in-this-section"></a>Dans cette section  
 [Instanciation de l’éditeur de base à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Fournit des instructions pas à pas sur la façon d’utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> pour créer une instance de l’éditeur principal.  
  
 [Accès à la mémoire tampon du texte à l’aide de l’API héritée](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Décrit le rôle de la mémoire tampon de texte dans l’éditeur principal, explique les systèmes associés qui sont utilisés pour accéder à la mémoire tampon et fournit une liste des interfaces implémentées par l’objet de mémoire tampon de texte, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 [Événements de la mémoire tampon du texte dans l’API héritée](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Fournit une liste des interfaces utilisées pour la notification des événements de mémoire tampon de texte.  
  
 [Guide pratique pour s’inscrire aux événements de mémoire tampon de texte avec l’API héritée](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Décrit comment signaler des événements de mémoire tampon de texte.  
  
 [Utilisation du gestionnaire de texte pour surveiller les paramètres globaux](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Explique comment le gestionnaire de texte est utilisé pour partager des informations de préférence globales avec les principaux composants de l’éditeur et comment recevoir des notifications d’événements Text Manager.  
  
 [Accès à la vue texte à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Décrit le rôle de l’affichage de texte dans l’éditeur principal et répertorie les interfaces implémentées par l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objet.  
  
 [Personnalisation des fenêtres de code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Fournit des informations sur l’utilisation d’une fenêtre de code pour encadrer l’affichage de texte, explique comment le gestionnaire de fenêtre de code est utilisé pour fournir des décorations à la fenêtre de code et fournit des notifications de nouvelles vues.  
  
 [Modification des paramètres d’affichage à l’aide de l’API héritée](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Fournit des instructions pas à pas sur la façon de forcer les paramètres d’affichage et la suppression des paramètres forcés.  
  
 [Services linguistiques et éditeur de base](../extensibility/language-services-and-the-core-editor.md)  
 Décrit l’instanciation d’un service de langage pour contrôler les décorations de code.  
  
## <a name="related-sections"></a>Sections connexes  
 [Procédure pas à pas : création d’un éditeur de base et inscription d’un type de fichier d’éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Fournit des instructions pas à pas sur le démarrage de l’éditeur principal à partir du code managé.  
  
 [Barre déroulante](../extensibility/drop-down-bar.md)  
 Explique comment la barre déroulante est utilisée dans la fenêtre de code et décrit les interfaces qui sont utilisées lors de l’implémentation d’une barre déroulante.  
  
 [Utilisation de marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Explique le concept des marqueurs de texte et la façon dont ils sont utilisés dans l’éditeur principal, et répertorie les interfaces utilisées pour accéder aux marqueurs de texte et les gérer.  
  
 [Guide pratique pour ajouter des marqueurs de texte standard](../extensibility/how-to-add-standard-text-markers.md)  
 Fournit des instructions pas à pas sur la création d’un marqueur de texte et sur l’ajout d’une commande personnalisée à un menu contextuel.  
  
 [Guide pratique pour créer des marqueurs de texte personnalisés](../extensibility/how-to-create-custom-text-markers.md)  
 Fournit des instructions pas à pas sur la création d’un marqueur de texte personnalisé et sur la façon de fournir le type de marqueur en tant que service.
