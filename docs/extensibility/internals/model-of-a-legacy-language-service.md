---
title: Modèle d’un service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b87106060d3fd66b3659f5d49159ebbb9be9ef6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726388"
---
# <a name="model-of-a-legacy-language-service"></a>Modèle d’un service de langage hérité
Un service de langage définit les éléments et les fonctionnalités d’un langage spécifique, et est utilisé pour fournir à l’éditeur des informations spécifiques à ce langage. Par exemple, l’éditeur doit connaître les éléments et les mots clés du langage afin de prendre en charge la coloration syntaxique.

 Le service de langage fonctionne étroitement avec la mémoire tampon de texte gérée par l’éditeur et la vue qui contient l’éditeur. L’option **Info Express** de Microsoft IntelliSense est un exemple de fonctionnalité fournie par un service de langage.

## <a name="a-minimal-language-service"></a>Service de langage minimal
 Le service de langage le plus basique contient les deux objets suivants :

- Le *service de langage* implémente l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>. Un service de langage contient des informations sur la langue, notamment son nom, son extension de nom de fichier, son gestionnaire de fenêtre de code et Coloriseur.

- *Coloriseur* implémente l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.

  Le dessin conceptuel suivant illustre un modèle de service de langage de base.

  ![Graphique du modèle de service de langage](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Modèle de service de langage de base

  La fenêtre de document héberge la *vue de document* de l’éditeur, dans le cas présent, l’éditeur de base [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. La vue de document et la mémoire tampon de texte sont détenues par l’éditeur. Ces objets fonctionnent avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] par le biais d’une fenêtre de document spécialisée appelée *fenêtre de code*. La fenêtre de code est contenue dans un objet <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> qui est créé et contrôlé par l’IDE.

  Lorsqu’un fichier avec une extension donnée est chargé, l’éditeur localise le service de langage associé à cette extension et lui passe la fenêtre de code en appelant la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>. Le service de langage retourne un *Gestionnaire de fenêtre de code*qui implémente l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>.

  Le tableau suivant fournit une vue d’ensemble des objets dans le modèle.

| Composant | Objet | Fonction |
|------------------| - | - |
| Mémoire tampon de texte | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Flux de texte en lecture/écriture Unicode. Il est possible que du texte utilise d’autres encodages. |
| Fenêtre Code | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Fenêtre de document qui contient un ou plusieurs affichages de texte. Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est en mode d’interface multidocument (MDI, multiple-document interface), la fenêtre de code est un enfant MDI. |
| Affichage de texte | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Fenêtre qui permet à l’utilisateur de parcourir et d’afficher du texte à l’aide du clavier et de la souris. Un affichage de texte apparaît pour l’utilisateur en tant qu’éditeur. Vous pouvez utiliser des affichages de texte dans des fenêtres d’éditeur ordinaires, dans la fenêtre sortie et dans la fenêtre exécution. En outre, vous pouvez configurer un ou plusieurs affichages de texte dans une fenêtre de code. |
| Gestionnaire de texte | Géré par le service <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>, à partir duquel vous obtenez un pointeur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> | Composant qui gère les informations communes partagées par tous les composants décrits précédemment. |
| Service de langage | Implémentation dépendante ; implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Objet qui fournit à l’éditeur des informations spécifiques au langage, telles que la mise en surbrillance de la syntaxe, la saisie semi-automatique des instructions et la correspondance des accolades. |

## <a name="see-also"></a>Voir aussi
- [Données de documents et affichage de documents dans les éditeurs personnalisés](../../extensibility/document-data-and-document-view-in-custom-editors.md)