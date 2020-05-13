---
title: Interfaces de service linguistique de l’héritage (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d80d6961f5eaf91721567ccb0efa73bbe31406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707381"
---
# <a name="legacy-language-service-interfaces"></a>Interfaces du service de langage hérité
Pour n’importe quel langage de programmation particulier, il ne peut y avoir qu’un seul exemple d’un service linguistique à la fois. Cependant, un seul service linguistique peut servir plus d’un éditeur.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]n’associe pas un service linguistique à un éditeur en particulier. Par conséquent, lorsque vous demandez une opération de service linguistique, vous devez identifier l’éditeur approprié comme un paramètre.

## <a name="common-interfaces-associated-with-language-services"></a>Interfaces communes associées aux services linguistiques
 L’éditeur obtient votre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> service linguistique en faisant appel à l’emballage VS approprié. La pièce d’identité de service (SID) adoptée dans cet appel identifie le service linguistique demandé.

 Vous pouvez implémenter les interfaces de service linguistique de base sur n’importe quel nombre de classes distinctes. Cependant, une approche commune consiste à mettre en œuvre les interfaces suivantes dans une seule classe :

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (facultatif)

  L’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> doit être implémentée sur tous les services linguistiques. Il fournit des informations sur votre service linguistique, tels que le nom localisé de la langue, les extensions de nom de fichier associés au service linguistique, et comment récupérer un coloriseur.

## <a name="additional-language-service-interfaces"></a>Interfaces de service linguistique supplémentaires
 D’autres interfaces peuvent être fournies avec votre service linguistique. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]demande une instance distincte de ces interfaces pour chaque cas du tampon de texte. Par conséquent, vous devez implémenter chacune de ces interfaces sur son propre objet. Le tableau suivant affiche les interfaces qui nécessitent une instance par instance tampon de texte.

|Interface|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Gère les parures de fenêtre de code, telles que la barre de dépôt. Vous pouvez obtenir cette <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> interface en utilisant la méthode. Il y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> en a un par fenêtre de code.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colorise les mots-clés et les délimitations linguistiques. Vous pouvez obtenir cette <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> interface en utilisant la méthode. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>est appelé à l’heure de la peinture. Évitez le travail à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> forte intensité de calcul à l’intérieur ou les performances pourraient en souffrir.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fournit des outils de paramètre IntelliSense. Lorsque le service linguistique reconnaît un caractère qui indique que les données de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> méthode doivent être affichées, comme une parenthèse ouverte, il appelle la méthode pour aviser la vue de texte que le service linguistique est prêt à afficher un outil d’information paramètreTip. La vue de texte rappelle ensuite dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> service de langue en utilisant les méthodes de l’interface pour obtenir les informations requises pour afficher la boîte à outils.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fournit l’achèvement de l’instruction IntelliSense. Lorsque le service linguistique est prêt à afficher <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> une liste d’achèvement, il appelle la méthode sur la vue textuelle. La vue de texte rappelle alors de nouveau <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> dans le service de langue en utilisant des méthodes sur l’objet.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Permet de modifier la vue de texte à l’aide du gestionnaire de commande. La classe dans laquelle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> vous implémentez l’interface doit également implémenter l’interface. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> La vue de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> texte récupère l’objet en interrogeant l’objet <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> qui est passé dans la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode. Il devrait <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> y avoir un objet pour chaque vue.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepte les commandes que l’utilisateur tape dans la fenêtre de code. Surveillez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> sortie de votre implémentation pour fournir des informations d’achèvement personnalisées et afficher la modification<br /><br /> Pour transmettre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> votre objet à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>vue du texte, appelez .|

## <a name="see-also"></a>Voir aussi
- [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Liste de vérification : création d’un service de langage hérité](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
