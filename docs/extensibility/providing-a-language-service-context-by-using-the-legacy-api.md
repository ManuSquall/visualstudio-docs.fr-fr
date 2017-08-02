---
title: "Fournir un contexte de Service de langage à l’aide de l’API héritée | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 10221f77e65acfb91c625c2f711b5804b64f827e
ms.lasthandoff: 02/22/2017

---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Fournir un contexte de Service de langage à l’aide de l’API héritée
Il existe deux options pour un service de langage fournir le contexte de l’utilisateur à l’aide du [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur de base : fournissent un contexte de marqueur de texte, ou fournir un contexte utilisateur tous les. Les différences sont décrites ici.  
  
 Pour plus d’informations sur la fourniture de contexte à un service de langage qui est connecté à votre propre éditeur, consultez [Comment : fournir un contexte pour les éditeurs de](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Fournir un contexte de marqueur de texte à l’éditeur  
 Pour fournir un contexte pour les erreurs du compilateur indiqués par des marqueurs de texte dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’éditeur de base, implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> Dans ce scénario, le service de langage fournit le contexte uniquement lorsque le curseur se trouve sur un marqueur de texte. Cela permet à l’éditeur fournir le mot clé au niveau du curseur à la **aide dynamique** fenêtre sans attributs.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Fournir tout le contexte utilisateur de l’éditeur  
 Si vous créez un service de langage et que vous utilisez la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] base éditeur, vous pourrez ensuite implémenter les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>interface pour fournir un contexte pour votre service de langage.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
 Pour l’implémentation de `IVsLanguageContextProvider`, un conteneur de contexte (collection) est associé à l’éditeur, qui est responsable de la mise à jour du conteneur de contexte. Lors de la **aide dynamique** fenêtre appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>interface sur ce conteneur de contexte en période d’inactivité, le sac de contextes interroge l’éditeur pour une mise à jour.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> L’éditeur notifie ensuite le service de langage qu’il convient de mettre à jour l’éditeur et passe un pointeur vers le conteneur de contexte. Cela est effectué en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>méthode à partir de l’éditeur pour le service de langage.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> En utilisant le pointeur vers le conteneur de contexte, le service de langage permettre désormais ajouter et supprimer des mots clés et des attributs. Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
 Il existe deux façons d’implémenter `IVsLanguageContextProvider`:  
  
-   Fournir un mot clé pour le conteneur de contexte  
  
     Lorsque l’éditeur est appelé pour mettre à jour le sac de contextes, passer dans les attributs et les mots clés appropriés, puis revenez `S_OK`. Cette valeur de retour indique à l’éditeur pour conserver votre contexte de mots clés et les attributs plutôt que de fournir le mot clé au niveau du curseur au jeu de contexte.  
  
-   Obtenir le mot clé à partir du mot clé à l’emplacement du curseur  
  
     Lorsque l’éditeur est appelé pour mettre à jour le conteneur de contexte, transmettez les attributs appropriés, puis revenez `E_FAIL`. Cette valeur de retour indique à l’éditeur pour conserver vos attributs dans le sac de contextes, mais mettre à jour le conteneur de contexte avec le mot clé à l’emplacement du curseur.  
  
 Le diagramme suivant illustre la façon dont le contexte est fourni pour un service de langage qui implémente `IVsLanguageContextProvider`.  
  
 ![Graphique de LangServiceImplementation2](~/extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
Contexte d’un service de langage  
  
 Comme vous pouvez le voir dans le diagramme, le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur de texte de base a un sac de contextes associé. Ce sac de contextes pointe vers trois conteneurs sous-contexte distincts : service de langage, l’éditeur par défaut et marqueur de texte. Langage service et texte marqueur sous-contexte sacs contiennent des attributs et des mots clés pour le service de langage si la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>est implémentée et des marqueurs de texte si la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>est implémentée.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> Si vous n’implémentez pas une de ces interfaces, l’éditeur fournit de contexte pour le mot clé à l’emplacement du curseur dans le sac de son éditeur par défaut.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Instructions de contexte pour les éditeurs et concepteurs  
 Concepteurs et éditeurs doivent fournir un mot clé général de l’éditeur ou de la fenêtre du concepteur. Cela est fait afin qu’affiche une rubrique d’aide générique, mais il est nécessaire, pour le concepteur ou l’éditeur lorsqu’un utilisateur appuie sur F1. Un éditeur doit, en outre, fournissez le mot clé en cours au niveau du curseur ou fournir un terme clé en fonction de la sélection actuelle. Pour cela, pour vous assurer qu’une rubrique d’aide pour le texte ou l’élément d’interface utilisateur désigné ou sélectionné s’affiche lorsque l’utilisateur appuie sur F1. Un concepteur fournit un contexte d’un élément sélectionné dans un concepteur, tel qu’un bouton sur un formulaire. Éditeurs et les concepteurs doivent également se connecter à un service de langage comme indiqué dans [hérité Language Service Essentials](../extensibility/internals/legacy-language-service-essentials.md).
