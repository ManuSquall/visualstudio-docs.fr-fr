---
title: "Interfaces de Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 925b504d8cba4813631d4f8ba6f7dbd9750f5eae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-interfaces"></a>Interfaces de Service de langage hérité
Pour n’importe quel langage de programmation particulier, il peut être qu’une seule instance d’un service de langage à la fois. Toutefois, un service de langage unique peut servir plusieurs éditeurs.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]n’associe pas d’un service de langage à n’importe quel éditeur particulier. Par conséquent, lorsque vous demandez une opération de service de langage, vous devez identifier l’éditeur approprié en tant que paramètre.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Interfaces courantes associées aux Services de langage  
 L’éditeur obtient votre service de langage en appelant <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> sur le VSPackage approprié. L’ID (SID) passée dans cet appel de service identifie le service de langage demandé.  
  
 Vous pouvez implémenter les interfaces de service de langage core sur n’importe quel nombre de classes distincts. Toutefois, une approche courante consiste à implémenter les interfaces suivantes dans une classe unique :  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock>(facultatif)  
  
 Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface doit être implémentée sur tous les services de langage. Il fournit des informations sur votre service de langage, telles que le nom localisé de la langue, les extensions de nom de fichier associées avec le service de langage et comment récupérer un Coloriseur.  
  
## <a name="additional-language-service-interfaces"></a>Interfaces de Service de langage supplémentaires  
 Autres interfaces peuvent être fournies avec votre service de langage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]demande une instance distincte de ces interfaces pour chaque instance de la mémoire tampon de texte. Par conséquent, vous devez implémenter chacun de ces interfaces sur son propre objet. Le tableau suivant montre les interfaces qui nécessitent une instance par instance de mémoire tampon de texte.  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Gère des ornements de fenêtre de code, tels que la barre de la liste déroulante. Vous pouvez obtenir cette interface en utilisant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> (méthode). Il y a un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> par la fenêtre de code.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colore les délimiteurs et les mots clés de langage. Vous pouvez obtenir cette interface en utilisant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> (méthode). <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>est appelée au moment de la peinture. Éviter de travail à l’intérieur de calculs intensifs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> ou performances Impossible d’en pâtir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fournit des info-bulles du paramètre IntelliSense. Lorsque le service de langage reconnaît un caractère qui indique que les données (méthode) doit être affiché, par exemple une parenthèse ouvrante, il appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> méthode pour notifier le texte qui permet d’afficher le service de langage est prêt à afficher une info-bulle des informations de paramètre. L’affichage de texte rappelle ensuite le service de langage à l’aide des méthodes de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface à obtenir les informations requises pour afficher l’info-bulle.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fournit la saisie semi-automatique des instructions IntelliSense. Lorsque le service de langage est prêt à afficher une liste de saisie semi-automatique, il appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode sur l’affichage de texte. L’affichage de texte rappelle ensuite le service de langage à l’aide des méthodes sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> objet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Autorise la modification de l’affichage de texte à l’aide du Gestionnaire de commandes. La classe dans laquelle vous implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interface doit également implémenter le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. L’affichage de texte récupère le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objet en interrogeant le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objet qui a été passée dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> (méthode). Il doit y avoir une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objet pour chaque vue.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepte des commandes que l’utilisateur tape dans la fenêtre de code. Surveiller la sortie à partir de votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> mise en œuvre pour fournir des informations d’achèvement personnalisé et afficher la modification<br /><br /> Pour passer votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objet de l’affichage de texte, appel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un Service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Liste de vérification : création d’un service de langage hérité](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)