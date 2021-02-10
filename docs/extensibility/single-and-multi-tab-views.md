---
title: Vues à onglet unique et à plusieurs onglets | Microsoft Docs
description: Découvrez comment implémenter des vues à plusieurs onglets dans des éditeurs, comme des fenêtres d’éditeur de code et un concepteur de formulaires.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6cea04557fb0bf3075461b22979cac2168af322
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942982"
---
# <a name="single-and-multi-tab-views"></a>Vues à onglet unique et onglets multiples
Un éditeur peut créer différents types de vues. Par exemple, une fenêtre de l’éditeur de code, une autre est un concepteur de formulaires.

 Une vue à plusieurs onglets est une vue avec plusieurs onglets. Par exemple, l’éditeur HTML a deux onglets en bas : **conception** et **source**, chacun d’entre eux étant une vue logique. Le mode Design affiche une page Web rendue, tandis que l’autre affiche le code HTML qui comprend la page Web.

## <a name="accessing-physical-views"></a>Accès aux vues physiques
 Les vues physiques hébergent des objets de vue de document, chacun représentant une vue des données dans la mémoire tampon, comme du code ou un formulaire. En conséquence, chaque objet de vue de document possède une vue physique (identifiée par une chaîne de vue physique) et, en général, une vue logique unique.

 Dans certains cas, toutefois, une vue physique peut avoir deux vues logiques ou plus. Il peut s’agir, par exemple, d’un éditeur doté d’une fenêtre fractionnée avec vues côte à côte ou d’un concepteur de formulaires doté d’une interface utilisateur graphique/conception et d’une vue code-behind-the-Form.

 Pour permettre à votre éditeur d’accéder à toutes les vues physiques disponibles, vous devez créer une chaîne de vue physique unique pour chaque type d’objet de vue de document que votre fabrique d’éditeur peut créer. Par exemple, la [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] fabrique d’éditeur peut créer des objets de vue de document pour une fenêtre de code et une fenêtre de concepteur de formulaires.

## <a name="creating-multi-tabbed-views"></a>Création de vues à onglets multiples
 Bien qu’un objet de vue de document doive être associé à une vue physique par le biais d’une chaîne de vue physique unique, vous pouvez placer plusieurs onglets dans l’affichage physique pour permettre l’affichage des données de différentes façons. Dans cette configuration à plusieurs onglets, tous les onglets sont associés à la même chaîne de vue physique, mais chaque onglet reçoit un GUID de vue logique différent.

 Pour créer un affichage à plusieurs onglets pour un éditeur, implémentez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> interface, puis associez un GUID de vue logique différent ( <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID> ) à chaque onglet que vous créez.

 L’éditeur HTML de Visual Studio est un exemple d’un éditeur avec un affichage à plusieurs onglets. Il possède des onglets de **conception** et de **source** . Pour ce faire, une autre vue logique est associée à chaque onglet, `LOGICALVIEWID_TextView` pour l’onglet **conception** et `LOGICALVIEWID_Code` pour l’onglet **source** .

 En spécifiant la vue logique appropriée, un VSPackage peut accéder à la vue qui correspond à un objectif particulier, telle que la conception d’un formulaire, la modification de code ou le débogage de code. Toutefois, l’une des fenêtres doit être identifiée par la chaîne NULL et doit correspondre à la vue logique principale ( `LOGVIEWID_Primary` ).

 Le tableau suivant répertorie les valeurs d’affichage logique disponibles et leur utilisation.

|GUID LOGVIEWID|Utilisation recommandée|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Vue par défaut/principale de la fabrique d’éditeur.<br /><br /> Toutes les fabriques d’éditeur doivent prendre en charge cette valeur. Cette vue doit utiliser la chaîne NULL comme chaîne de vue physique. Au moins une vue logique doit être définie sur cette valeur.|
|`LOGVIEWID_Debugging`|Affichage du débogage. En général, `LOGVIEWID_Debugging` correspond à la même vue que `LOGVIEWID_Code` .|
|`LOGVIEWID_Code`|Affichage lancé par la commande **afficher le code** .|
|`LOGVIEWID_Designer`|Vue lancée par la commande **afficher le formulaire** .|
|`LOGVIEWID_TextView`|Affichage de l’éditeur de texte. Il s’agit de la vue qui retourne <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> , à partir de laquelle vous pouvez accéder <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|`LOGVIEWID_UserChooseView`|Invite l’utilisateur à choisir la vue à utiliser.|
|`LOGVIEWID_ProjectSpecificEditor`|Passé par la boîte de dialogue **Ouvrir avec** à<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Quand l’utilisateur choisit l’entrée « (éditeur de projet par défaut) ».|

 Bien que les GUID de vue logique soient extensibles, vous pouvez utiliser uniquement les GUID de vue logique définis dans le VSPackage.

 À l’arrêt, Visual Studio conserve le GUID de la fabrique d’éditeur et les chaînes de vue physiques associées à la fenêtre de document afin qu’il puisse être utilisé pour rouvrir les fenêtres de document lorsque la solution est rouverte. Seules les fenêtres qui sont ouvertes quand une solution est fermée sont conservées dans le fichier de solution (. suo). Ces valeurs correspondent aux `VSFPROPID_guidEditorType` valeurs et `VSFPROPID_pszPhysicalView` passées dans le `propid` paramètre de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> méthode.

## <a name="example"></a>Exemple
 Cet extrait de code illustre comment l' <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> objet est utilisé pour accéder à une vue qui implémente `IVsCodeWindow` . Dans ce cas, le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> service est utilisé pour appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> et demander `LOGVIEWID_TextView` , qui obtient un pointeur vers un frame de fenêtre. Un pointeur vers l’objet de vue de document est obtenu en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> et en spécifiant la valeur `VSFPROPID_DocView` . À partir de l’objet de vue de document, `QueryInterface` est appelé pour `IVsCodeWindow` . Dans ce cas, l’attente est qu’un éditeur de texte est retourné, de sorte que l’objet de vue de document retourné dans la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> méthode est une fenêtre de code.

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
