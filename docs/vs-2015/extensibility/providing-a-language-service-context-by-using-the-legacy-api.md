---
title: Fournir un contexte de service de langage à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4471b71b612008ba7d0733c92286415cd3c3f6b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193873"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Fournir un contexte de service linguistique à l’aide de l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Deux options permettent à un service de langage de fournir un contexte utilisateur à l’aide de l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur principal : fournissez un contexte de marqueur de texte ou fournissez tout le contexte utilisateur. Les différences entre les deux sont décrites ici.  
  
 Pour plus d’informations sur la fourniture de contexte à un service de langage connecté à votre propre éditeur, consultez Guide pratique [pour fournir un contexte aux éditeurs](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Fournir le contexte du marqueur de texte à l’éditeur  
 Pour fournir le contexte pour les erreurs de compilateur indiquées par des marqueurs de texte dans l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur principal, implémentez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface. Dans ce scénario, le service de langage fournit le contexte uniquement lorsque le curseur se trouve sur un marqueur de texte. Cela permet à l’éditeur de fournir le mot clé au curseur dans la fenêtre **d’aide dynamique** sans attributs.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Fournir tout le contexte utilisateur à l’éditeur  
 Si vous créez un service de langage et utilisez l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur de base, vous pouvez implémenter l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface pour fournir un contexte à votre service de langage.  
  
 Pour l’implémentation de `IVsLanguageContextProvider` , un conteneur de contexte (collection) est attaché à l’éditeur, qui est responsable de la mise à jour du conteneur de contexte. Lorsque la fenêtre **d’aide dynamique** appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> interface sur ce conteneur de contexte au moment de l’inactivité, le sac de contexte interroge l’éditeur pour obtenir une mise à jour. L’éditeur avertit ensuite le service de langage qu’il doit mettre à jour l’éditeur et passe un pointeur vers le conteneur de contexte. Pour ce faire, appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> méthode de l’éditeur au service de langage. À l’aide du pointeur vers le conteneur de contexte, le service de langage peut maintenant ajouter et supprimer des attributs et des mots clés. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Il existe deux façons d’implémenter `IVsLanguageContextProvider` :  
  
- Fournir un mot clé au conteneur de contexte  
  
   Lorsque l’éditeur est appelé pour mettre à jour le conteneur de contexte, transmettez les mots clés et attributs appropriés, puis retournez `S_OK` . Cette valeur de retour indique à l’éditeur de conserver votre mot clé et le contexte de l’attribut au lieu de fournir le mot clé au curseur au conteneur de contexte.  
  
- Obtenir le mot clé à partir du mot clé au niveau du curseur  
  
   Lorsque l’éditeur est appelé pour mettre à jour le conteneur de contexte, transmettez les attributs appropriés, puis retournez `E_FAIL` . Cette valeur de retour indique à l’éditeur de conserver vos attributs dans le conteneur de contexte, mais de mettre à jour le conteneur de contexte avec le mot clé au niveau du curseur.  
  
  Le diagramme suivant illustre la façon dont le contexte est fourni pour un service de langage qui implémente `IVsLanguageContextProvider` .  
  
  ![Graphique de LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  Contexte pour un service de langage  
  
  Comme vous pouvez le voir dans le diagramme, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] un sac de contexte est associé à l’éditeur de texte principal. Ce sac de contextes pointe vers trois conteneurs de sous-contextes distincts : le service de langage, l’éditeur par défaut et le marqueur de texte. Les conteneurs de sous-contexte du service de langage et du marqueur de texte contiennent des attributs et des mots clés pour le service de langage si l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface est implémentée, et des marqueurs de texte si l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface est implémentée. Si vous n’implémentez pas l’une de ces interfaces, l’éditeur fournit un contexte pour le mot clé au niveau du curseur dans le conteneur de sous-contexte de l’éditeur par défaut.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Instructions de contexte pour les éditeurs et les concepteurs  
 Les concepteurs et les éditeurs doivent fournir un mot clé général pour la fenêtre de l’éditeur ou du concepteur. Cette opération est effectuée afin qu’une rubrique d’aide générique, mais appropriée, s’affiche pour le concepteur ou l’éditeur lorsqu’un utilisateur appuie sur la touche F1. Un éditeur doit, en plus de cela, fournir le mot clé actuel au curseur ou fournir un terme clé en fonction de la sélection actuelle. Cela permet de s’assurer qu’une rubrique d’aide pour le texte ou l’élément d’interface utilisateur pointé ou sélectionné s’affiche lorsque l’utilisateur appuie sur la touche F1. Un concepteur fournit un contexte pour un élément sélectionné dans un concepteur, tel qu’un bouton sur un formulaire. Les éditeurs et les concepteurs doivent également se connecter à un service de langage comme indiqué dans [Legacy Language Service Essentials](../extensibility/internals/legacy-language-service-essentials.md).
