---
title: Vues simples et multi-onglets Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c308b4d6c7b90456255019ef57c6b9d544aefc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699991"
---
# <a name="single-and-multi-tab-views"></a>Vues à onglet unique et onglets multiples
Un éditeur peut créer différents types de vues. Un exemple est une fenêtre d’éditeur de code, un autre est un concepteur de formulaires.

 Une vue multi-tabbed est une vue qui a plusieurs onglets. Par exemple, l’éditeur HTML a deux onglets en bas : **Design** and **Source**, chacun une vue logique. La vue de conception affiche une page Web rendue, tandis que l’autre affiche le HTML qui comprend la page Web.

## <a name="accessing-physical-views"></a>Accès aux vues physiques
 Les vues physiques hébergent des objets de vue de document, chacun représentant une vue des données dans le tampon, tel que le code ou un formulaire. Par conséquent, chaque objet de vue de document a une vue physique (identifiée par quelque chose connu sous le nom de chaîne de vue physique), et généralement une vue logique unique.

 Dans certains cas, cependant, une vue physique peut avoir deux points de vue ou plus logiques. Certains exemples sont un éditeur qui a une fenêtre divisée avec des vues côte à côte, ou un concepteur de formulaires qui a une vue DE GUI/ conception et une vue de code-derrière-la-forme.

 Pour permettre à votre éditeur d’accéder à toutes les vues physiques disponibles, vous devez créer une chaîne de vue physique unique pour chaque type d’objet de vue de document que votre usine d’éditeur peut créer. Par exemple, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] l’usine d’éditeurs peut créer des objets de vue de document pour une fenêtre de code et une fenêtre de concepteur de formulaires.

## <a name="creating-multi-tabbed-views"></a>Création de vues multi-tabbed
 Bien qu’un objet de vue de document doit être associé à une vue physique à travers une chaîne de vue physique unique, vous pouvez placer plusieurs onglets dans la vue physique pour permettre la visualisation des données de différentes manières. Dans cette configuration multi-tabbed, tous les onglets sont associés à la même chaîne de vue physique, mais chaque onglet est donné une vue logique différente GUID.

 Pour créer une vue multi-tabbed pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> un éditeur, implémenter<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>l’interface, puis associer une vue logique différente GUID ( ) avec chaque onglet que vous créez.

 L’éditeur HTML visual Studio est un exemple d’éditeur avec une vue multi-onglets. Il a des onglets **Design** et **Source.** Pour ce faire, une vue logique différente `LOGICALVIEWID_TextView` est associée `LOGICALVIEWID_Code` à chaque onglet, pour **l’onglet Conception** et pour l’onglet **Source.**

 En spécifiant la vue logique appropriée, un VSPackage peut accéder à la vue qui correspond à un but particulier, comme la conception d’un formulaire, l’édition de code ou le code de débogage. Cependant, l’une des fenêtres doit être identifiée par la chaîne`LOGVIEWID_Primary`NULL, ce qui doit correspondre à la vue logique primaire ( ).

 Le tableau suivant répertorie les valeurs de vue logique disponibles et leur utilisation.

|LOGVIEWID GUID|Utilisation recommandée|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Vue par défaut/primaire de l’usine d’éditeurs.<br /><br /> Toutes les usines de rédacteurs doivent soutenir cette valeur. Cette vue doit utiliser la chaîne NULL comme chaîne de vue physique. Au moins un point de vue logique doit être défini à cette valeur.|
|`LOGVIEWID_Debugging`|Vue de débogage. Typiquement, `LOGVIEWID_Debugging` cartes à la `LOGVIEWID_Code`même vue que .|
|`LOGVIEWID_Code`|Afficher la commande **View Code.**|
|`LOGVIEWID_Designer`|Vue lancée par la commande **View Form.**|
|`LOGVIEWID_TextView`|Vue d’éditeur de texte. C’est la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>vue qui revient <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, à partir de laquelle vous pouvez accéder .|
|`LOGVIEWID_UserChooseView`|Invite l’utilisateur à choisir la vue à utiliser.|
|`LOGVIEWID_ProjectSpecificEditor`|Passé par **l’Open With** dialog box à<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> lorsque l’utilisateur choisit l’entrée " (éditeur par défaut de projet)".|

 Bien que les GUIDs de vue logique soient extensibles, vous ne pouvez utiliser que les GUIDs logiques définis dans votre VSPackage.

 À l’arrêt, Visual Studio conserve le GUID de l’usine d’éditeur et les chaînes de vue physique associées à la fenêtre de document afin qu’il puisse être utilisé pour rouvrir les fenêtres de documents lorsque la solution est rouverte. Seules les fenêtres ouvertes lorsqu’une solution est fermée sont persistantes dans le fichier solution (.suo). Ces valeurs correspondent `VSFPROPID_guidEditorType` `VSFPROPID_pszPhysicalView` au et `propid` aux valeurs <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> passées dans le paramètre de la méthode.

## <a name="example"></a>Exemple
 Cet extrait illustre comment l’objet <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> est utilisé pour accéder `IVsCodeWindow`à une vue qui implémente . Dans ce cas, le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> service <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> est `LOGVIEWID_TextView`utilisé pour appeler et demander , qui obtient un pointeur à un cadre de fenêtre. Un pointeur de l’objet de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> vue de document `VSFPROPID_DocView`est obtenu en appelant et en spécifiant une valeur de . De l’objet `QueryInterface` de vue `IVsCodeWindow`de document, est demandé . Dans ce cas, on s’attend à ce qu’un éditeur <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> de texte soit retourné, et donc l’objet de vue de document retourné dans la méthode est une fenêtre de code.

```cpp
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)
{
  HRESULT hr;
  if (NULL == szFile || !*szFile)
    return E_INVALIDARG;

  if (iLine == -1L)
    return S_FALSE;

  VSITEMID                  itemid;
  VARIANT                   var;
  RECT                      rc;
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;
  IVsCodeWindow *           pCodeWin    = NULL;
  IVsTextView *             pTextView   = NULL;
  IVsUIHierarchy *          pHierarchy  = NULL;
  IVsWindowFrame *          pFrame      = NULL;
  IUnknown *                pUnk        = NULL;
  IVsHighlight *            pHighlight  = NULL;

  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));
  pFrame->Show();
  VariantInit(&var);
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }
  pUnk = V_UNKNOWN(&var);
  if (NULL != pUnk)
  {
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )
    {
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);
      // uncover selection
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));
      UncoverSelectionRect(&rc);
    }
  }

Error:
  CLEARINTERFACE(pHighlight);
  CLEARINTERFACE(pTextView);
  CLEARINTERFACE(pCodeWin);
  CLEARINTERFACE(pUnk);
  CLEARINTERFACE(pFrame);
  CLEARINTERFACE(pOpenDoc);
  CLEARINTERFACE(pHierarchy);
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);
  return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [Prise en charge de vues de document multiples](../extensibility/supporting-multiple-document-views.md)
- [Guide pratique pour joindre des vues à des données de document](../extensibility/how-to-attach-views-to-document-data.md)
- [Création d’éditeurs et de concepteurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)
