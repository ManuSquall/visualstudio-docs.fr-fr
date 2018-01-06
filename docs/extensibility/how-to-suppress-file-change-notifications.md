---
title: "Comment : supprimer les Notifications de modification de fichier | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 209006129bcb2cfaaf88233768df1d9597cd09a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-suppress-file-change-notifications"></a>Comment : supprimer les Notifications de modification de fichier
Lorsque le fichier physique qui représente la mémoire tampon de texte a été modifié, une boîte de dialogue s’affiche avec le message **vous souhaitez enregistrer les modifications apportées aux éléments suivants ?** Il s’agit en tant que notification de modification de fichier. Si de nombreuses modifications doivent se trouver dans le fichier, toutefois, cette boîte de dialogue Affichage indéfiniment peut rapidement devenir ennuyeux.  
  
 Vous pouvez supprimer par programme de cette boîte de dialogue à l’aide de la procédure suivante. Ce faisant, vous pouvez recharger un fichier immédiatement sans avoir à inviter l’utilisateur à enregistrer les modifications apportées à chaque fois.  
  
### <a name="to-suppress-file-change-notification"></a>Pour supprimer la notification de modification de fichier  
  
1.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> méthode pour déterminer quel objet de mémoire tampon de texte est associé à votre fichier ouvert.  
  
2.  Direct le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet qui est analyse en mémoire pour ignorer les modifications du fichier en obtenant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> à partir de l’interface le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet (données de document), puis en implémentant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> méthode avec le `fIgnore` paramètre la valeur `true`.  
  
3.  Appeler les méthodes sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaces pour mettre à jour de la mémoire <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet avec les modifications de fichier (par exemple, lorsqu’un champ est ajouté à votre composant).  
  
4.  Mettre à jour le fichier sur disque avec les modifications sans prendre en compte les modifications de que l’utilisateur est peut-être en cours d’exécution en attente.  
  
     De cette façon, lorsque vous dirigez la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> des notifications de modifications d’objet pour reprendre la surveillance pour le fichier, la mémoire tampon de texte dans la mémoire reflète les modifications que vous avez créé, ainsi que toutes les autres modifications en attente. Le fichier sur le disque reflète le dernier code généré par vous et les précédemment enregistrement les modifications apportées par l’utilisateur dans le code utilisateur a été modifié.  
  
5.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> méthode pour notifier le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet reprendre la surveillance pour les notifications de modification de fichier en définissant le `fIgnore` paramètre `false`.  
  
6.  Si vous prévoyez d’effectuer plusieurs modifications au fichier, comme dans le cas du contrôle de code source (SCC), vous devez indiquer le service de modification de fichier global suspendre temporairement les notifications de modification de fichier.  
  
     Par exemple, si vous réécrivez le fichier et que vous modifiez l’horodatage, vous devez suspendre les notifications de modification de fichier, comme les opérations de réécriture et timestample chaque nombre comme événement de changement d’un fichier distinct. Pour activer la notification de modification de fichier global vous appelez plutôt la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> (méthode).  
  
## <a name="example"></a>Exemple  
 La liste suivante montre comment supprimer la notification de modification de fichier.  
  
```cpp  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>Programmation fiable  
 Si votre cas implique plusieurs modifications au fichier, comme dans le cas du contrôle de code source, il est important de reprendre les notifications de modification de fichier global avant la génération d’alertes de données de document pour reprendre la surveillance des modifications de fichier.