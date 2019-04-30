---
title: Modèle d’un Service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a044d623931d024f15baba1532e3a563273242e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860098"
---
# <a name="model-of-a-legacy-language-service"></a>Modèle d’un service de langage hérité
Un service de langage définit les éléments et les fonctionnalités pour une langue spécifique et est utilisé pour fournir l’éditeur avec les informations spécifiques à cette langue. Par exemple, l’éditeur doit connaître les éléments et les mots clés du langage pour prendre en charge la coloration syntaxique.

 Le service de langage travaille en étroite collaboration avec la mémoire tampon de texte géré par l’éditeur et la vue qui contienne l’éditeur. Microsoft IntelliSense **Info Express** option est un exemple d’une fonctionnalité fournie par un service de langage.

## <a name="a-minimal-language-service"></a>Un Service de langage Minimal
 Le service de langage plus simple contient les deux objets suivants :

- Le *service de langage* implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface. Un service de langage a des informations sur le langage, y compris son nom, les extensions de nom de fichier, Gestionnaire de fenêtres de code et Coloriseur.

- Le *Coloriseur* implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface.

  Le schéma conceptuel suivant montre un modèle d’un service de langage de base.

  ![Graphique de modèle de Service de langage](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") modèle de service de langage de base

  Les hôtes de fenêtre de document le *vue du document* de l’éditeur, dans ce cas le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] éditeur principal. La vue de document et la mémoire tampon de texte sont détenus par l’éditeur. Ces objets fonctionnent avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] via une fenêtre de document spécialisé appelé un *fenêtre de code*. La fenêtre de code est contenue dans un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objet qui est créé et contrôlé par l’IDE.

  Quand un fichier avec une extension donnée est chargé, l’éditeur localise le service de langage associé à cette extension et la transmet à la fenêtre de code en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> (méthode). Le service de langage retourne un *Gestionnaire de fenêtres de code*, qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface.

  Le tableau suivant fournit une vue d’ensemble des objets dans le modèle.

| Composant | Object | Fonction |
|------------------| - | - |
| Mémoire tampon de texte | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Un flux de texte Unicode en lecture/écriture. Il est possible pour le texte à utiliser d’autres encodages. |
| Fenêtre Code | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Une fenêtre de document qui contient une ou plusieurs vues de texte. Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est en mode d’interface multidocument (MDI), la fenêtre de code est un enfant MDI. |
| Affichage de texte | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Une fenêtre qui permet à l’utilisateur accéder et afficher le texte à l’aide du clavier et la souris. Un affichage de texte apparaît à l’utilisateur en tant qu’éditeur. Vous pouvez utiliser les affichages de texte dans les fenêtres de l’éditeur ordinaires, la fenêtre Sortie et la fenêtre exécution. En outre, vous pouvez configurer une ou plusieurs vues de texte dans une fenêtre de code. |
| Gestionnaire de texte | Géré par le <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> de service, à partir duquel vous obtenez une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> pointeur | Un composant qui gère les informations courantes partagées par tous les composants décrits précédemment. |
| service de langage | Implémentation dépendante ; implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Objet qui fournit l’éditeur avec les informations spécifiques au langage telles que la coloration syntaxique, la saisie semi-automatique des instructions et la correspondance d’accolade. |

## <a name="see-also"></a>Voir aussi
- [Données de documents et affichage de documents dans les éditeurs personnalisés](../../extensibility/document-data-and-document-view-in-custom-editors.md)