---
title: À l’intérieur de l’éditeur principal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81d91603d6c365946b1064cac3a7f1ca3c1e6ba8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713293"
---
# <a name="inside-the-core-editor"></a>À l’intérieur de l’éditeur principal
Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal est un ensemble de plusieurs composants qui vous permettent de modifier et interroger des informations textuelles. Si vous avez personnalisé l’éditeur principal à l’aide de l’API héritée, vous pouvez continuer à utiliser ces personnalisations, qui seront acheminées via les adaptateurs d’éditeur. Il est recommandé, cependant, que vous deviez adapter vos personnalisations vers le nouvel éditeur API.

 Les domaines suivants sont des aspects importants de l’éditeur principal :

-   Mémoire tampon de texte

-   Affichage de texte

-   Fenêtre Code

-   Marqueurs de texte

-   Gestionnaire de texte

-   Intégration avec les services de langage

## <a name="in-this-section"></a>Dans cette section
- [Instancier l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md) fournit des instructions détaillées sur l’utilisation <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> pour créer une instance de la base éditeur.

- [Accéder à la mémoire tampon de texte à l’aide de l’API héritée](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) explique le rôle de la mémoire tampon de texte dans l’éditeur principal, explique les systèmes associés qui sont utilisés pour accéder à la mémoire tampon et fournit une liste des interfaces implémentées par l’objet de mémoire tampon de texte, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.

- [Événements de mémoire tampon de texte dans l’API héritée](../extensibility/text-buffer-events-in-the-legacy-api.md) fournit une liste des interfaces qui sont utilisées pour la notification des événements de mémoire tampon de texte.

- [Guide pratique pour Enregistrer les événements de mémoire tampon de texte avec l’API héritée](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md) décrit comment signaler les événements de mémoire tampon de texte.

- [Utilisez le Gestionnaire de texte pour surveiller les paramètres globaux](../extensibility/using-the-text-manager-to-monitor-global-settings.md) explique comment le Gestionnaire de texte permet de partager des informations de préférence global avec les principaux composants de l’éditeur et comment recevoir des notifications d’événements du Gestionnaire de texte.

- [Accéder aux theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) décrit le rôle de la vue de texte dans l’éditeur principal et répertorie les interfaces implémentées par le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objet.

- [Personnaliser les fenêtres de code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md) fournit des informations sur comment une fenêtre de code est utilisée pour encadrer l’affichage de texte, explique comment le Gestionnaire de fenêtres de code sert à fournir des ornements à la fenêtre de code et fournit une notification de nouvelles vues .

- [Modifier les paramètres d’affichage à l’aide de l’API héritée](../extensibility/changing-view-settings-by-using-the-legacy-api.md) fournit des instructions sur comment forcer les paramètres d’affichage et suppression des paramètres forcés.

- [Services de langage et de l’éditeur principal](../extensibility/language-services-and-the-core-editor.md) décrit l’instanciation d’un service de langage pour les ornements de code de contrôle.

## <a name="related-sections"></a>Rubriques connexes
- [Procédure pas à pas : Créer un cœur éditeur et l’inscription d’un type de fichier éditeur](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md) fournit des instructions détaillées sur la façon de démarrer l’éditeur principal à partir du code managé.

- [Barre déroulante](../extensibility/drop-down-bar.md) explique comment la barre déroulante est utilisée dans la fenêtre de code et décrit les interfaces qui sont utilisées lorsque vous implémentez une barre déroulante.

- [Utiliser des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md) explique le concept des marqueurs de texte et comment elles sont utilisées dans l’éditeur principal et répertorie les interfaces qui sont utilisées pour accéder et gérer des marqueurs de texte.

- [Guide pratique pour Ajouter des marqueurs de texte standard](../extensibility/how-to-add-standard-text-markers.md) fournit des instructions détaillées sur la création d’un marqueur de texte et comment ajouter une commande personnalisée à un menu contextuel.

- [Guide pratique pour Créer des marqueurs de texte personnalisé](../extensibility/how-to-create-custom-text-markers.md) fournit des instructions détaillées sur la création d’un marqueur de texte personnalisé et comment fournir le type de marqueur en tant que service.