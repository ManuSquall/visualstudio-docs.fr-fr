---
title: 'Procédure : Supprimer les Notifications de modification de fichier | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47647910b53b5f86b828ec87c62019b76204f124
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078367"
---
# <a name="how-to-suppress-file-change-notifications"></a>Procédure : Supprimer les notifications de modification de fichier
Lorsque le fichier physique qui représente la mémoire tampon a été modifié, une boîte de dialogue s’affiche avec le message **voulez-vous enregistrer les modifications apportées aux éléments suivants ?** Il s’agit en tant que notification de modification de fichier. Si de nombreuses modifications vont être dans le fichier, cependant, cette boîte de dialogue Affichage indéfiniment peut rapidement devenir ennuyeux.

 Vous pouvez supprimer par programmation de cette boîte de dialogue à l’aide de la procédure suivante. En le supprimant de la boîte de dialogue, vous pouvez recharger un fichier immédiatement sans avoir à inviter l’utilisateur à enregistrer les modifications chaque fois.

## <a name="to-suppress-file-change-notification"></a>Pour supprimer la notification de modification de fichier

1. Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> méthode pour déterminer quel objet de mémoire tampon de texte est associé à votre fichier ouvert.

2. Direct le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet qui est analyse en mémoire pour ignorer les modifications de fichiers en obtenant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> interface à partir de la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet (données de document), puis en implémentant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> méthode avec le `fIgnore` paramètre la valeur `true`.

3. Appelez les méthodes sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaces pour mettre à jour de la mémoire <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet avec les modifications de fichier (par exemple, lorsqu’un champ est ajouté à votre composant).

4. Mettre à jour le fichier sur disque avec les modifications sans prendre en compte les modifications de que l’utilisateur est peut-être en cours d’exécution en attente.

     De cette façon, lorsque vous dirigez la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> notifications de modification d’objet pour reprendre l’analyse de fichier, la mémoire tampon en mémoire reflète les modifications que vous avez généré. La mémoire tampon en mémoire reflète également toutes les autres modifications en attente. Le fichier sur le disque reflète le code le plus récent généré par vos soins et toute enregistrée précédemment des modifications apportées par l’utilisateur dans le code utilisateur a été modifié.

5. Appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> méthode pour informer le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet pour reprendre la surveillance pour les notifications de modification de fichier en définissant le `fIgnore` paramètre `false`.

6. Si vous envisagez d’apporter plusieurs modifications au fichier, comme dans le cas du contrôle de code source (SCC), vous devez indiquer le service de modification de fichier global suspendre temporairement les notifications de modification de fichier.

     Par exemple, si vous réécrivez le fichier et que vous modifiez l’horodatage, vous devez suspendre les notifications de modification de fichier, car les opérations réécriture et timestamp comptent comme un événement de modification de fichier distinct. Pour activer la notification de modification de fichier global, vous devez plutôt appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> (méthode).

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment supprimer la notification de modification de fichier.

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