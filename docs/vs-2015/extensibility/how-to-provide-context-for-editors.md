---
title: 'Comment : fournir le contexte pour les éditeurs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11a98599a9812cd00650d113170ff55c01ac44db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839613"
---
# <a name="how-to-provide-context-for-editors"></a>Guide pratique : fournir un contexte pour les éditeurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour un éditeur, le contexte est actif uniquement lorsque l’éditeur a le focus ou avait le focus juste avant le déplacement du focus vers une fenêtre outil. Vous pouvez fournir le contexte d’un éditeur en procédant comme suit :  
  
1. Créez un conteneur de contexte.  
  
2. Publiez le conteneur de contexte sur l’identificateur d’élément de sélection (SEID).  
  
3. Conservez le contexte dans le conteneur.  
  
   Ces tâches sont couvertes par les procédures suivantes. Pour plus d’informations sur la fourniture de contexte, consultez **programmation robuste** plus loin dans cette rubrique.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Pour créer un conteneur de contexte pour un éditeur ou un concepteur  
  
1. Appelez `QueryService` sur votre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface pour le <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> service.  
  
     Un pointeur vers l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> interface est retourné.  
  
2. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> méthode pour créer un nouveau conteneur de contexte ou de sous-contexte.  
  
     Un pointeur vers l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> interface est retourné.  
  
3. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> méthode pour ajouter des attributs, des mots clés de recherche ou des mots clés F1 au conteneur de contexte ou de sous-contexte.  
  
4. Si vous créez un conteneur de sous-contexte, appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> méthode pour lier le conteneur de sous-contexte au conteneur de contexte parent.  
  
5. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> pour recevoir une notification lorsque la fenêtre **d’aide dynamique** va être mise à jour.  
  
     Si vous souhaitez que la fenêtre **d’aide dynamique** appelle votre éditeur lorsqu’elle est prête à être mise à jour, vous pouvez différer la modification du contexte jusqu’à ce que la mise à jour se produise. Cela peut améliorer les performances, car cela vous permet de retarder les algorithmes qui prennent du temps jusqu’à ce que le temps d’inactivité du système soit disponible.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Pour publier le conteneur de contexte dans SEID  
  
1. Appelez `QueryService` sur le <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> service pour retourner un pointeur vers l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interface.  
  
2. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> , en spécifiant une `elementid` valeur d’identificateur d’élément (paramètre) de SEID_UserContext pour indiquer que vous passez le contexte au niveau global.  
  
3. Lorsque l’éditeur ou le concepteur devient actif, les valeurs de son <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> objet sont propagées à la sélection globale. Vous n’avez besoin de terminer ce processus qu’une seule fois par session, puis de stocker le pointeur vers le contexte global créé lors de l’appel de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> .  
  
### <a name="to-maintain-the-context-bag"></a>Pour conserver le conteneur de contexte  
  
1. Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> pour garantir que la fenêtre **d’aide dynamique** appelle l’éditeur ou le concepteur avant de mettre à jour.  
  
     Pour chaque sac de contexte qui a appelé <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> une fois le conteneur de contexte créé et implémenté <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> , l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> pour notifier au fournisseur de contexte que le conteneur de contexte sera mis à jour. Vous pouvez utiliser cet appel pour modifier les attributs et les mots clés dans le conteneur de contexte et dans tous les conteneurs de sous-contexte avant que la mise à jour de la fenêtre **d’aide dynamique** ne se produise.  
  
2. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> sur le conteneur de contexte pour indiquer que l’éditeur ou le concepteur a un nouveau contexte.  
  
     Lorsque la fenêtre **d’aide dynamique** appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> pour indiquer qu’elle est en état de mise à jour, l’éditeur ou le concepteur peut mettre à jour le contexte de manière appropriée pour le conteneur de contexte parent et tous les conteneurs de sous-contexte à ce moment-là.  
  
    > [!NOTE]
    > L' `SetDirty` indicateur est défini automatiquement à `true` chaque fois que le contexte est ajouté ou supprimé dans le conteneur de contexte. La fenêtre **d’aide dynamique** appelle uniquement <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> sur le conteneur de contexte si l' `SetDirty` indicateur a la valeur `true` . Elle est réinitialisée à `false` après la mise à jour.  
  
3. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> pour ajouter un contexte à la collection de contexte active ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> pour supprimer le contexte.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Si vous écrivez votre propre éditeur, vous devez effectuer les trois procédures décrites dans cette rubrique pour fournir le contexte de l’éditeur.  
  
> [!NOTE]
> Pour activer correctement une fenêtre de l’éditeur ou du concepteur et vérifier que le routage des commandes est correctement mis à jour, vous devez appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> sur le composant pour en faire la fenêtre de focus.  
  
 Le SEID est une collection de propriétés qui changent en fonction de la sélection. Les informations de SEID sont disponibles via la sélection globale. La sélection globale est connectée à des événements déclenchés par l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interface et contient une liste de tous les éléments sélectionnés (éditeur actuel, fenêtre outil active, hiérarchie actuelle, etc.).  
  
 Pour les éditeurs et les concepteurs, dans lesquels le contexte peut changer chaque fois que le curseur se déplace dans un mot, il est inefficace de mettre constamment à jour le conteneur de contexte. Pour améliorer l’efficacité de la mise à jour chaque fois que vous détectez le curseur qui se déplace dans la fenêtre de l’éditeur ou du concepteur, vous pouvez appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> . Cela vous permet de conserver vos modifications de contexte jusqu’à ce qu’il y ait du temps d’inactivité et que le service de contexte de l’IDE envoie une notification à l’éditeur ou au concepteur que la fenêtre **d’aide dynamique** met à jour. Cette approche est utilisée dans la procédure « pour maintenir le sac de contexte » dans cette rubrique.  
  
 Après avoir fourni un contexte pour les activités au sein de votre éditeur ou concepteur, vous devez fournir un mot clé F1 spécifique pour permettre aux utilisateurs d’obtenir de l’aide pour l’éditeur ou le concepteur lui-même.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
