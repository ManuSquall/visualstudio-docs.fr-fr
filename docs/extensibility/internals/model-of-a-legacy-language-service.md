---
title: Modèle d’un service de langage hérité | Microsoft Docs
description: Utilisez ce modèle de service de langage minimal pour l’éditeur de base de Visual Studio comme guide pour la création de votre propre service de langage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 26b27bd6bef40a38e32e5b0d6d26e3d147659286
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954637"
---
# <a name="model-of-a-legacy-language-service"></a>Modèle d’un service de langage hérité
Un service de langage définit les éléments et les fonctionnalités d’un langage spécifique, et est utilisé pour fournir à l’éditeur des informations spécifiques à ce langage. Par exemple, l’éditeur doit connaître les éléments et les mots clés du langage afin de prendre en charge la coloration syntaxique.

 Le service de langage fonctionne étroitement avec la mémoire tampon de texte gérée par l’éditeur et la vue qui contient l’éditeur. L’option **Info Express** de Microsoft IntelliSense est un exemple de fonctionnalité fournie par un service de langage.

## <a name="a-minimal-language-service"></a>Service de langage minimal
 Le service de langage le plus basique contient les deux objets suivants :

- Le *service de langage* implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface. Un service de langage contient des informations sur la langue, notamment son nom, son extension de nom de fichier, son gestionnaire de fenêtre de code et Coloriseur.

- *Coloriseur* implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface.

  Le dessin conceptuel suivant illustre un modèle de service de langage de base.

  ![Graphique du modèle de service de langage](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Modèle de service de langage de base

  La fenêtre de document héberge la *vue de document* de l’éditeur, dans ce cas l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] éditeur principal. La vue de document et la mémoire tampon de texte sont détenues par l’éditeur. Ces objets fonctionnent avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] une fenêtre de document spécialisée appelée *fenêtre de code*. La fenêtre de code est contenue dans un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objet qui est créé et contrôlé par l’IDE.

  Lorsqu’un fichier avec une extension donnée est chargé, l’éditeur localise le service de langage associé à cette extension et lui passe la fenêtre de code en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> méthode. Le service de langage retourne un *Gestionnaire de fenêtre de code* qui implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface.

  Le tableau suivant fournit une vue d’ensemble des objets dans le modèle.

| Composant | Object | Fonction |
|------------------| - | - |
| Mémoire tampon de texte | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Flux de texte en lecture/écriture Unicode. Il est possible que du texte utilise d’autres encodages. |
| Fenêtre de code | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Fenêtre de document qui contient un ou plusieurs affichages de texte. Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est en mode d’interface multidocument (MDI, multiple-document interface), la fenêtre de code est un enfant MDI. |
| Affichage de texte | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Fenêtre qui permet à l’utilisateur de parcourir et d’afficher du texte à l’aide du clavier et de la souris. Un affichage de texte apparaît pour l’utilisateur en tant qu’éditeur. Vous pouvez utiliser des affichages de texte dans des fenêtres d’éditeur ordinaires, dans la fenêtre sortie et dans la fenêtre exécution. En outre, vous pouvez configurer un ou plusieurs affichages de texte dans une fenêtre de code. |
| Gestionnaire de texte | Géré par le <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> service, à partir duquel vous obtenez un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> pointeur | Composant qui gère les informations communes partagées par tous les composants décrits précédemment. |
| Service de langage | Implémentation dépendante ; implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Objet qui fournit à l’éditeur des informations spécifiques au langage, telles que la mise en surbrillance de la syntaxe, la saisie semi-automatique des instructions et la correspondance des accolades. |

## <a name="see-also"></a>Voir aussi
- [Données de documents et affichage de documents dans les éditeurs personnalisés](../../extensibility/document-data-and-document-view-in-custom-editors.md)
