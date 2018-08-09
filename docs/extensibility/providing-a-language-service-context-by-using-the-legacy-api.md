---
title: Fournissant un contexte de Service de langage à l’aide de l’API héritée | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9daef780847da99463811a9c10399102dc7b808
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637430"
---
# <a name="provide-a-language-service-context-by-using-the-legacy-api"></a>Fournir un contexte de service de langage à l’aide de l’API héritée
Il existe deux options pour un service de langage fournir le contexte de l’utilisateur à l’aide la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal : fournir un contexte de marqueur de texte, ou fournir tout le contexte utilisateur. Les différences sont décrites ici.  
  
 Pour plus d’informations sur la fourniture de contexte à un service de langage qui est connecté à votre propre éditeur, consultez [Comment : fournir un contexte pour les éditeurs](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Fournir le contexte de marqueur de texte à l’éditeur  
 Pour fournir un contexte pour les erreurs du compilateur indiqués par les marqueurs de texte dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur de base, implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface. Dans ce scénario, le service de langage fournit le contexte uniquement lorsque le curseur se trouve sur un marqueur de texte. Ainsi, l’éditeur de fournir le mot clé au niveau du curseur à la **aide dynamique** fenêtre sans attributs.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Fournir tout le contexte utilisateur à l’éditeur  
 Si vous créez un service de langage et que vous utilisez le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] core éditeur, puis vous pouvez implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface pour fournir un contexte pour votre service de langage.  
  
 Pour l’implémentation de `IVsLanguageContextProvider`, un conteneur de contexte (collection) est attaché à l’éditeur, qui est responsable de la mise à jour le conteneur de contexte. Lorsque le **aide dynamique** fenêtre appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> interface sur ce conteneur de contexte en période d’inactivité, le conteneur de contexte interroge l’éditeur pour une mise à jour. L’éditeur notifie ensuite le service de langage qu’il convient de mettre à jour l’éditeur et passe un pointeur vers le conteneur de contexte. Cela est effectué en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> méthode à partir de l’éditeur pour le service de langage. En utilisant le pointeur au conteneur de contexte, le service de langage permettre désormais ajouter et supprimer des attributs et mots clés. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Il existe deux façons d’implémenter `IVsLanguageContextProvider`:  
  
-   Fournir un mot clé pour le conteneur de contexte  
  
     Lorsque l’éditeur est appelé pour mettre à jour le conteneur de contexte, transmettez dans les attributs et les mots clés appropriés, puis revenez `S_OK`. Cette valeur de retour indique à l’éditeur pour conserver votre mot clé et attribut au contexte plutôt que de fournir le mot clé au niveau du curseur vers le sac de contextes.  
  
-   Obtenir le mot clé à partir du mot clé au niveau du curseur  
  
     Lorsque l’éditeur est appelé pour mettre à jour le conteneur de contexte, transmettez les attributs appropriés, puis revenez `E_FAIL`. Cette valeur de retour indique à l’éditeur pour conserver vos attributs dans le sac de contextes, mais mettre à jour le conteneur de contexte avec le mot clé au niveau du curseur.  
  
 Le diagramme suivant illustre la façon dont le contexte est fourni pour un service de langage qui implémente `IVsLanguageContextProvider`.  
  
 ![Graphique de LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
Contexte pour un service de langage  
  
 Comme vous pouvez le voir dans le diagramme, le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principal éditeur de texte a un sac de contextes attaché. Ce conteneur de contexte pointe vers trois conteneurs de sous-contexte distincts : service de langage, l’éditeur par défaut et marqueur de texte. Le langage service et le texte marqueur de sous-contexte contienne des attributs et mots clés pour le service de langage si le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface est implémentée et des marqueurs de texte si le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface est implémentée. Si vous n’implémentez pas une de ces interfaces, l’éditeur fournit de contexte pour le mot clé au niveau du curseur dans le conteneur de sous-contexte éditeur par défaut.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Instructions de contexte pour les éditeurs et les concepteurs  
 Concepteurs et éditeurs doivent fournir un mot clé général pour l’éditeur ou de la fenêtre du concepteur. Cette opération est effectuée afin qu’affiche une rubrique d’aide générique, mais il est nécessaire, pour le concepteur ou l’éditeur quand un utilisateur appuie sur **F1**. Un éditeur doit, en outre, fournissez le mot clé actuel au niveau du curseur ou fournissez un terme clé basé sur la sélection actuelle. Cela est fait pour vous assurer qu’une rubrique d’aide pour le texte ou d’un élément d’interface utilisateur désigné ou sélectionnées s’affichent lorsque l’utilisateur appuie sur **F1**. Un concepteur fournit un contexte d’un élément sélectionné dans un concepteur, tel qu’un bouton sur un formulaire. Éditeurs et concepteurs doivent également se connecter à un service de langage comme indiqué dans [essentials de service de langage hérité](../extensibility/internals/legacy-language-service-essentials.md).