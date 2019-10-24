---
title: Interfaces du service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 065ef972709ca78b516a9acc5f4a737d2963e4b7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726844"
---
# <a name="legacy-language-service-interfaces"></a>Interfaces du service de langage hérité
Pour un langage de programmation particulier, il ne peut y avoir qu’une seule instance d’un service de langage à la fois. Toutefois, un service de langage unique peut servir plusieurs éditeurs.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] n’associe pas un service de langage à un éditeur spécifique. Par conséquent, lorsque vous demandez une opération de service de langage, vous devez identifier l’éditeur approprié en tant que paramètre.

## <a name="common-interfaces-associated-with-language-services"></a>Interfaces courantes associées aux services de langage
 L’éditeur obtient votre service de langage en appelant <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> sur le VSPackage approprié. L’ID de service (SID) passé dans cet appel identifie le service de langage demandé.

 Vous pouvez implémenter les interfaces du service de langage principal sur un nombre quelconque de classes distinctes. Toutefois, une approche courante consiste à implémenter les interfaces suivantes dans une classe unique :

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (facultatif)

  L’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> doit être implémentée sur tous les services de langage. Il fournit des informations sur votre service de langage, telles que le nom localisé de la langue, les extensions de nom de fichier associées au service de langage et la récupération d’un Coloriseur.

## <a name="additional-language-service-interfaces"></a>Interfaces du service de langage supplémentaire
 D’autres interfaces peuvent être fournies avec votre service de langage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] demande une instance distincte de ces interfaces pour chaque instance de la mémoire tampon de texte. Par conséquent, vous devez implémenter chacune de ces interfaces sur son propre objet. Le tableau suivant présente les interfaces qui requièrent une instance par instance de mémoire tampon de texte.

|Interface|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Gère les ornements de fenêtre de code, tels que la barre déroulante. Vous pouvez accéder à cette interface à l’aide de la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>. Il y a une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> par fenêtre de code.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colore les mots clés de langage et les délimiteurs. Vous pouvez accéder à cette interface à l’aide de la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> est appelée au moment de la peinture. Évitez les tâches nécessitant beaucoup de calculs à l’intérieur des <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> ou des performances.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fournit des info-bulles de paramètres IntelliSense. Lorsque le service de langage reconnaît un caractère qui indique que les données de méthode doivent être affichées, telles qu’une parenthèse ouvrante, il appelle la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> pour notifier l’affichage de texte que le service de langage est prêt à afficher une info-bulle d’informations sur les paramètres. L’affichage de texte rappelle ensuite le service de langage à l’aide des méthodes de l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> pour obtenir les informations nécessaires à l’affichage de l’info-bulle.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fournit la saisie semi-automatique des instructions IntelliSense. Lorsque le service de langage est prêt à afficher une liste de saisie semi-automatique, il appelle la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> sur l’affichage de texte. L’affichage de texte rappelle ensuite le service de langage à l’aide de méthodes sur l’objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Autorise la modification de l’affichage de texte à l’aide du gestionnaire de commandes. La classe dans laquelle vous implémentez l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> doit également implémenter l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. L’affichage de texte récupère l’objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> en interrogeant l’objet <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> passé dans la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>. Il doit y avoir un objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> pour chaque vue.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepte les commandes que l’utilisateur tape dans la fenêtre de code. Surveiller la sortie de votre implémentation de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pour fournir des informations de saisie semi-automatique personnalisées et modifier l’affichage<br /><br /> Pour passer votre objet <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> à l’affichage de texte, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|

## <a name="see-also"></a>Voir aussi
- [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Liste de vérification : création d’un service de langage hérité](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)