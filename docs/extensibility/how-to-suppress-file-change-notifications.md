---
title: "Comment : supprimer les Notifications de modification de fichier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - supprimer la notification de modification de fichier"
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Comment : supprimer les Notifications de modification de fichier
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque le fichier physique qui représente la mémoire tampon de texte a été modifié, des affichages d'une boîte de dialogue avec le message **Voulez \-vous enregistrer les modifications apportées aux éléments suivants ?** Ceci constitue la notification de modification du fichier.  Si beaucoup de modifications vont être au fichier, toutefois, cette boîte de dialogue affichant maintes et maintes reprises peut rapidement devenir problématique.  
  
 Vous pouvez supprimer par programme cette boîte de dialogue à l'aide de la procédure suivante.  Ce faisant, vous pouvez recharger un fichier immédiatement sans devoir demander à l'utilisateur d'enregistrer les modifications apportées à chaque fois.  
  
### Pour supprimer la notification de modification du fichier  
  
1.  Appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> pour déterminer l'objet de mémoire tampon de texte est associé à votre fichier ouvert.  
  
2.  Réexécutez l'objet d' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> en mémoire pour ignorer les modifications apportées au fichier d'analyse à obtenir l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> de l'objet d' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> \(données de le document\), puis implémentation de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> avec le jeu de paramètres d' `fIgnore` à `true`.  
  
3.  Appelez les méthodes sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> et les interfaces d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pour mettre à jour l'objet en mémoire d' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> avec les modifications de fichier \(par exemple lorsqu'un champ est ajouté à votre composant\).  
  
4.  Mettez à jour le fichier sur le disque avec les modifications sans prendre en compte les modifications en attente que l'utilisateur peut avoir en cours.  
  
     De cette façon, lorsque vous exécutez l'objet d' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> à l'analyse de synthèse pour les notifications de modification du fichier, la mémoire tampon de texte dans la mémoire reflète les modifications que vous avez générées, ainsi que toutes les autres modifications en attente.  Le fichier sur le disque reflète le dernier code généré par et vous les modifications apportées précédemment stockés par l'utilisateur de code utilisateur\-modifié.  
  
5.  Appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> pour informer l'objet d' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> à l'analyse de synthèse pour les notifications de changement de fichier en affectant au paramètre la valeur d' `fIgnore` à `false`.  
  
6.  Si vous projetez d'apporter plusieurs modifications au fichier, comme dans le cas de le contrôle \(SCC\) de code source, il de vous devez demander au service de modification du fichier global d'interrompre temporairement des notifications de changement de fichier.  
  
     Par exemple, si vous réécrivez le fichier puis modifiez l'horodatage, vous devez suspendre les notifications de changement de fichier, comme opérations de réécriture et de timestample chaque nombre un événement de modification du fichier séparé.  Pour activer la notification de modification du fichier globale vous devez à la place appeler la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> .  
  
## Exemple  
 Les éléments suivants montrent comment supprimer la notification de modification du fichier.  
  
```cpp#  
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
  
## Programmation fiable  
 Si votre cas comprend plusieurs modifications apportées au fichier, comme dans le cas de SCC, puis de il est important de continuer des notifications de changement de fichier globales avant d'avertir les données du document à l'analyse de résumé pour le fichier change.