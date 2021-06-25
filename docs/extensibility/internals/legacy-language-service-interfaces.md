---
title: Interfaces du service de langage hérité | Microsoft Docs
description: Découvrez les interfaces disponibles dans le kit de développement logiciel (SDK) Visual Studio qui fournissent des fonctionnalités de service de langage héritées.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 75697e1d212b24b743fed62284b384985749fe7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898602"
---
# <a name="legacy-language-service-interfaces"></a>Interfaces du service de langage hérité
Pour un langage de programmation particulier, il ne peut y avoir qu’une seule instance d’un service de langage à la fois. Toutefois, un service de langage unique peut servir plusieurs éditeurs.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] n’associe pas un service de langage à un éditeur particulier. Par conséquent, lorsque vous demandez une opération de service de langage, vous devez identifier l’éditeur approprié en tant que paramètre.

## <a name="common-interfaces-associated-with-language-services"></a>Interfaces courantes associées aux services de langage
 L’éditeur obtient votre service de langage en appelant <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> sur le VSPackage approprié. L’ID de service (SID) passé dans cet appel identifie le service de langage demandé.

 Vous pouvez implémenter les interfaces du service de langage principal sur un nombre quelconque de classes distinctes. Toutefois, une approche courante consiste à implémenter les interfaces suivantes dans une classe unique :

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (facultatif)

  L' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface doit être implémentée sur tous les services de langage. Il fournit des informations sur votre service de langage, telles que le nom localisé de la langue, les extensions de nom de fichier associées au service de langage et la récupération d’un Coloriseur.

## <a name="additional-language-service-interfaces"></a>Interfaces du service de langage supplémentaire
 D’autres interfaces peuvent être fournies avec votre service de langage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] demande une instance distincte de ces interfaces pour chaque instance de la mémoire tampon de texte. Par conséquent, vous devez implémenter chacune de ces interfaces sur son propre objet. Le tableau suivant présente les interfaces qui requièrent une instance par instance de mémoire tampon de texte.

|Interface|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Gère les ornements de fenêtre de code, tels que la barre déroulante. Vous pouvez accéder à cette interface à l’aide de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> méthode. Il y en a une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> par fenêtre de code.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colore les mots clés de langage et les délimiteurs. Vous pouvez accéder à cette interface à l’aide de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> est appelée au moment de la peinture. Évitez les tâches nécessitant beaucoup de calculs à l’intérieur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> ou aux performances.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fournit des info-bulles de paramètres IntelliSense. Lorsque le service de langage reconnaît un caractère qui indique que les données de méthode doivent être affichées, telles qu’une parenthèse ouvrante, il appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> méthode pour notifier à la vue de texte que le service de langage est prêt à afficher une info-bulle d’informations sur les paramètres. L’affichage de texte rappelle ensuite le service de langage en utilisant les méthodes de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface pour obtenir les informations nécessaires pour afficher l’info-bulle.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fournit la saisie semi-automatique des instructions IntelliSense. Lorsque le service de langage est prêt à afficher une liste de saisie semi-automatique, il appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode sur la vue de texte. L’affichage de texte rappelle ensuite le service de langage à l’aide de méthodes sur l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> objet.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Autorise la modification de l’affichage de texte à l’aide du gestionnaire de commandes. La classe dans laquelle vous implémentez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interface doit également implémenter l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. L’affichage de texte récupère l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objet en interrogeant l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objet passé dans la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode. Il doit y avoir un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objet pour chaque vue.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepte les commandes que l’utilisateur tape dans la fenêtre de code. Surveiller la sortie de votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implémentation pour fournir des informations de saisie semi-automatique personnalisées et modifier l’affichage<br /><br /> Pour passer votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objet à l’affichage de texte, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .|

## <a name="see-also"></a>Voir aussi
- [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Checklist : création d’un service de langage hérité](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
