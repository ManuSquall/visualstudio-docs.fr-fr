---
title: 'Procédure : supprimer les notifications de modification de fichier | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f045175eae165b75a887ada2716b19f34fc228b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204080"
---
# <a name="how-to-suppress-file-change-notifications"></a>Guide pratique pour supprimer les notifications de modification de fichier
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque le fichier physique représentant la mémoire tampon de texte a été modifié, une boîte de dialogue s’affiche avec le message **voulez-vous enregistrer les modifications apportées aux éléments suivants ?** C’est ce que l’on appelle la notification de modification de fichier. Toutefois, si de nombreuses modifications vont être apportées au fichier, cette boîte de dialogue s’affiche à nouveau plus rapidement.  
  
 Vous pouvez supprimer par programmation cette boîte de dialogue à l’aide de la procédure suivante. En procédant ainsi, vous pouvez recharger un fichier immédiatement sans avoir à inviter l’utilisateur à enregistrer les modifications à chaque fois.  
  
### <a name="to-suppress-file-change-notification"></a>Pour supprimer la notification de modification de fichier  
  
1. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> méthode pour déterminer l’objet de mémoire tampon de texte associé à votre fichier ouvert.  
  
2. Dirigez l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet en mémoire pour ignorer les modifications apportées au fichier d’analyse en obtenant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> interface à partir de l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet (données de document), puis en implémentant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> méthode avec le `fIgnore` paramètre défini sur `true` .  
  
3. Appelez les méthodes sur les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaces et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pour mettre à jour l’objet en mémoire <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> avec les modifications de fichier (par exemple, lorsqu’un champ est ajouté à votre composant).  
  
4. Mettez à jour le fichier sur le disque avec les modifications sans tenir compte des modifications en attente que l’utilisateur peut avoir en cours.  
  
     De cette façon, lorsque vous demandez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> à l’objet de reprendre l’analyse des notifications de modification de fichier, la mémoire tampon de texte en mémoire reflète les modifications que vous avez générées, ainsi que toutes les autres modifications en attente. Le fichier sur le disque reflète le code le plus récent généré par vous et les modifications précédemment enregistrées par l’utilisateur dans le code modifié par l’utilisateur.  
  
5. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> méthode pour indiquer à l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet de reprendre l’analyse des notifications de modification de fichier en affectant au paramètre la valeur `fIgnore` `false` .  
  
6. Si vous envisagez d’apporter plusieurs modifications au fichier, comme dans le cas du contrôle de code source (SCC), vous devez indiquer au service de modification de fichier global d’interrompre temporairement les notifications de modification de fichier.  
  
     Par exemple, si vous réécrivez le fichier, puis modifiez l’horodateur, vous devez suspendre les notifications de modification de fichier, car les opérations de réécriture et de timestample de chaque compte comme un événement de modification de fichier distinct. Pour activer la notification de modification de fichier globale, vous devez appeler la méthode à la place <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment supprimer la notification de modification de fichier.  
  
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
  
## <a name="robust-programming"></a>Programmation fiable  
 Si votre cas implique plusieurs modifications dans le fichier, comme dans le cas de SCC, il est important de reprendre les notifications de modification de fichier Global avant d’alerter les données de document pour reprendre l’analyse des modifications de fichier.
