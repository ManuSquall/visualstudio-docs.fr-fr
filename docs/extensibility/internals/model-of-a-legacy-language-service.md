---
title: Modèle d’un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f024a02641902843f673ce3ff8583a4bce3b135
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707048"
---
# <a name="model-of-a-legacy-language-service"></a>Modèle d’un service de langage hérité
Un service linguistique définit les éléments et les caractéristiques d’une langue spécifique et est utilisé pour fournir à l’éditeur des informations spécifiques à cette langue. Par exemple, l’éditeur doit connaître les éléments et les mots clés de la langue afin de prendre en charge la coloration syntaxe.

 Le service linguistique travaille en étroite collaboration avec le tampon de texte géré par l’éditeur et le point de vue qui contient l’éditeur. L’option Microsoft IntelliSense **Quick Info** est un exemple d’une fonctionnalité fournie par un service linguistique.

## <a name="a-minimal-language-service"></a>Un service de langue minimal
 Le service linguistique le plus basique contient les deux objets suivants :

- Le *service linguistique* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> implémente l’interface. Un service de langue a des informations sur la langue, y compris son nom, extensions de nom de fichier, gestionnaire de fenêtre de code, et colorier.

- Le *coloriste* implémente l’interface. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>

  Le dessin conceptuel suivant montre un modèle d’un service linguistique de base.

  ![Graphique du modèle de service linguistique](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Modèle de service linguistique de base

  La fenêtre de document héberge la *vue* de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] document de l’éditeur, dans ce cas, l’éditeur de base. La vue de document et le tampon de texte sont la propriété de l’éditeur. Ces objets [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fonctionnent avec à travers une fenêtre de document spécialisée appelée *une fenêtre de code*. La fenêtre de code <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> est contenue dans un objet qui est créé et contrôlé par l’IDE.

  Lorsqu’un fichier avec une extension donnée est chargé, l’éditeur localise le service linguistique <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> associé à cette extension et lui transmet la fenêtre de code en appelant la méthode. Le service de langue renvoie un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> gestionnaire de fenêtre de *code*, qui implémente l’interface.

  Le tableau suivant donne un aperçu des objets du modèle.

| Composant | Object | Fonction |
|------------------| - | - |
| Tampon de texte | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Un flux de texte Unicode lu/écrire. Il est possible pour le texte d’utiliser d’autres codages. |
| Fenêtre de code | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Une fenêtre de document qui contient une ou plusieurs vues de texte. Lorsqu’elle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est en mode interface multi-documents (MDI), la fenêtre de code est un enfant MDI. |
| Vue de texte | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Une fenêtre qui permet à l’utilisateur de naviguer et de visualiser le texte en utilisant le clavier et la souris. Une vue de texte apparaît à l’utilisateur en tant qu’éditeur. Vous pouvez utiliser des vues de texte dans les fenêtres ordinaires de l’éditeur, la fenêtre de sortie et la fenêtre immédiate. En outre, vous pouvez configurer une ou plusieurs vues de texte dans une fenêtre de code. |
| Gestionnaire de texte | Géré par <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> le service, à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> partir duquel vous obtenez un pointeur | Un composant qui conserve les informations communes partagées par tous les composants décrits précédemment. |
| Service linguistique | Mise en œuvre dépendante; Implémente<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Un objet qui fournit à l’éditeur des informations spécifiques à la langue telles que la mise en évidence de la syntaxe, l’achèvement des relevés et l’appariement des accolades. |

## <a name="see-also"></a>Voir aussi
- [Données de documents et affichage de documents dans les éditeurs personnalisés](../../extensibility/document-data-and-document-view-in-custom-editors.md)
