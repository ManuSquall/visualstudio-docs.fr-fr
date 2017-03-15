---
title: "Comment : fournir un contexte pour les éditeurs | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 17
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
ms.openlocfilehash: 362cd554e0723b1137d033440c9844d6cf3e59dd
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-context-for-editors"></a>Comment : fournir un contexte pour les éditeurs
Pour un éditeur, le contexte est actif uniquement lorsque l’éditeur a le focus ou avait le focus immédiatement avant le focus a été déplacé vers une fenêtre outil. Vous pouvez fournir le contexte pour un éditeur en procédant comme suit :  
  
1.  Créer un conteneur de contexte.  
  
2.  Publier le sac de contextes à l’identificateur d’élément de sélection (SEID).  
  
3.  Conserver le contexte dans le jeu.  
  
 Ces tâches sont couverts par les procédures suivantes. Pour plus d’informations sur la fourniture de contexte, consultez **programmation robuste** plus loin dans cette rubrique.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Pour créer un conteneur de contexte pour un éditeur ou un concepteur  
  
1.  Appelez `QueryService` sur votre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>d’interface pour le <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>service.</xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
     Un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>interface est renvoyé.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>  
  
2.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>pour créer un nouvel ensemble de contexte ou sous-contexte.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>  
  
     Un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>interface est renvoyé.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>  
  
3.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>pour ajouter des attributs, des mots clés de recherche ou des mots clés F1 au jeu de contexte ou sous-contexte.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>  
  
4.  Si vous créez un conteneur sous-contexte, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>méthode pour lier le sac sous-contexte le sac de contextes parent.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>  
  
5.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>pour recevoir une notification lorsque la **aide dynamique** fenêtre est sur le point de mise à jour.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>  
  
     Avoir le **aide dynamique** fenêtre appeler votre éditeur lorsqu’il est prêt à mettre à jour vous offre la possibilité de retarder la modification du contexte jusqu'à ce que la mise à jour se produit. Cela peut améliorer les performances car elle permet de différer l’exécution des algorithmes du temps jusqu'à ce que le temps d’inactivité système est disponible.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Pour publier le sac de contextes à la SEID  
  
1.  Appelez `QueryService` sur la <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>service renvoie un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> </xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>  
  
2.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, en spécifiant un identificateur d’élément (`elementid` paramètre) valeur de SEID_UserContext pour indiquer que vous passez un contexte au niveau global.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>  
  
3.  Lorsque l’éditeur ou un concepteur devient actif, les valeurs de ses <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>objet sont propagées à la sélection globale.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> Vous devez uniquement exécuter ce processus une fois par session, puis stocke le pointeur vers le contexte global créé lors de l’appel <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>  
  
### <a name="to-maintain-the-context-bag"></a>Pour maintenir le sac de contextes  
  
1.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>pour vous assurer que les **aide dynamique** fenêtre appelle l’éditeur ou le concepteur avant la mise à jour.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>  
  
     Pour chaque conteneur de contexte qui a appelé <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>après le conteneur de contexte est créé et a implémenté <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, les appels IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>pour notifier le fournisseur de contexte que le conteneur de contexte sera mis à jour.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> Vous pouvez utiliser cet appel pour modifier les attributs et les mots clés dans le conteneur de contexte et dans des sacs sous-contexte, avant la **aide dynamique** mise à jour de la fenêtre.  
  
2.  Appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>sur le sac de contextes pour indiquer que l’éditeur ou le concepteur a nouveau contexte.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>  
  
     Lors de la **aide dynamique** fenêtre appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>pour indiquer qu’elle est mise à jour, l’éditeur ou le concepteur peut mettre à jour le contexte appropriées pour le conteneur de contexte parent et des sacs sous-contexte à ce moment-là.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>  
  
    > [!NOTE]
    >  Le `SetDirty` est automatiquement défini à `true` chaque fois que le contexte est ajouté ou supprimé du conteneur de contexte de. Le **aide dynamique** fenêtre appelle uniquement <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>sur le conteneur de contexte si les `SetDirty` est défini à `true`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> Il est réinitialisé à `false` après la mise à jour.  
  
3.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>pour ajouter un contexte à la collection de contexte actif ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>pour supprimer le contexte.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>  
  
## <a name="robust-programming"></a>Programmation fiable  
 Si vous écrivez votre propre éditeur, vous devez effectuer les trois procédures dans cette rubrique pour fournir un contexte pour l’éditeur.  
  
> [!NOTE]
>  Pour activer correctement une fenêtre d’éditeur ou concepteur et pour vous assurer que le routage de commande est mis à jour correctement, vous devez appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>sur le composant pour rendre la fenêtre focus.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>  
  
 Le SEID est une collection de propriétés qui changent en fonction de la sélection. Informations de SEID sont disponibles via la sélection globale. La sélection globale est reliée à des événements déclenchés par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>interface, et a une liste de tous les éléments sélectionnés (éditeur actuel, fenêtre Outil active, hiérarchie actuelle et ainsi de suite).</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>  
  
 Pour les éditeurs et concepteurs, dans quel contexte peut changer à chaque fois que le curseur se déplace dans un mot, il est inutile d’actualiser en permanence le sac de contextes. Pour effectuer la mise à jour plus efficace chaque fois que vous détectez le curseur se déplace dans l’éditeur ou de la fenêtre du concepteur, vous pouvez appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> Cela permet de conserver vos changements de contexte jusqu'à ce qu’il est temps d’inactivité et de service du contexte de l’IDE envoie une notification à l’éditeur ou du concepteur qui le **aide dynamique** mise à jour de la fenêtre. Cette approche est utilisée dans la procédure « pour mettre à jour le sac de contextes » dans cette rubrique.  
  
 Après avoir entré le contexte pour les activités dans votre éditeur ou un concepteur, vous devez fournir un mot-clé F1 pour permettre aux utilisateurs d’obtenir de l’aide de l’éditeur ou le concepteur lui-même.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
