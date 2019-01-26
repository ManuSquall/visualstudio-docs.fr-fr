---
title: Vues uniques et multiples onglet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ee4c44cb23c8df5d0a7ea64c54cc37440eaa57c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014976"
---
# <a name="single-and-multi-tab-views"></a>Vues à onglet unique et onglets multiples
Un éditeur peut créer différents types de vues. Par exemple, une fenêtre d’éditeur de code, un autre est un concepteur de formulaires.  
  
 Une vue dotée de plusieurs onglets est une vue qui comporte plusieurs onglets. Par exemple, l’éditeur HTML comporte deux onglets en bas : **Conception** et **Source**, chacun une vue logique. La vue de conception affiche une page web affichée, tandis que l’autre affiche le code HTML qui comprend la page web.  
  
## <a name="accessing-physical-views"></a>Accès aux vues physiques  
 Les affichages physiques hébergent des objets de vue de document, représentant chacun une vue de données dans la mémoire tampon, tels que le code ou un formulaire. En conséquence, chaque objet de vue de document a une vue physique (identifié par un processus connu sous forme de chaîne vue physique) et généralement une seule vue logique.  
  
 Dans certains cas, cependant, une vue physique peut avoir deux ou plusieurs affichages logiques. Un éditeur qui a une fenêtre fractionnée avec des vues côte à côte, ou un concepteur de formulaires qui a une vue de l’interface graphique utilisateur/conception et une vue de code-behind-the-formulaire sont des exemples.  
  
 Pour activer votre éditeur afin d’accéder à toutes les vues physiques disponibles, vous devez créer une chaîne de la vue physique unique pour chaque type d’objet de vue de document que votre fabrique d’éditeur peut créer. Par exemple, le [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] fabrique d’éditeur peut créer le document des objets de vue pour une fenêtre de code et une fenêtre de Concepteur de formulaires.  
  
## <a name="creating-multi-tabbed-views"></a>Création de vues à plusieurs onglets  
 Si un objet de vue de document doit être associé à une vue physique dans une chaîne de la vue physique unique, vous pouvez placer plusieurs onglets dans la vue physique pour activer l’affichage des données de différentes façons. Dans cette configuration à plusieurs onglets, tous les onglets sont associés à la même chaîne de la vue physique, mais chaque onglet est donné à une autre vue logique GUID.  
  
 Pour créer une vue dotée de plusieurs onglets pour un éditeur, implémentez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> interface, puis associez une autre vue logique GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) avec chaque onglet que vous créez.  
  
 L’éditeur HTML de Visual Studio est un exemple d’un éditeur avec une vue d’onglet multiples. Il a **conception** et **Source** onglets. Pour ce faire, une vue logique différente est associée à chaque onglet, `LOGICALVIEWID_TextView` pour le **conception** onglet et `LOGICALVIEWID_Code` pour le **Source** onglet.  
  
 En spécifiant la vue logique appropriée, un VSPackage peut accéder à la vue qui correspond à un usage particulier, telles que la création d’un formulaire, modification du code ou le débogage de code. Toutefois, une des fenêtres doit être identifiée par la chaîne de valeur NULL et que ces valeurs doivent correspondre à la vue logique principale (`LOGVIEWID_Primary`).  
  
 Le tableau suivant répertorie les valeurs de la vue logique disponibles et leur utilisation.  
  
|GUID DE LOGVIEWID|Utilisation recommandée|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Affichage principal/par défaut de la fabrique d’éditeur.<br /><br /> Toutes les fabriques d’éditeur doivent prendre en charge cette valeur. Cette vue doit utiliser la chaîne de valeur NULL en tant que sa chaîne d’affichage physique. Au moins une vue logique doit être définie sur cette valeur.|  
|`LOGVIEWID_Debugging`|Affichage de débogage. En règle générale, `LOGVIEWID_Debugging` est mappé à la même vue en tant que `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Mode lancé par le **afficher le Code** commande.|  
|`LOGVIEWID_Designer`|Mode lancé par le **afficher le formulaire** commande.|  
|`LOGVIEWID_TextView`|Affichage de l’éditeur de texte. C’est la vue retourne <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, à partir de laquelle vous pouvez accéder à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Invite l’utilisateur à choisir la vue à utiliser.|  
|`LOGVIEWID_ProjectSpecificEditor`|Passé par le **ouvrir avec** boîte de dialogue<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Quand l’utilisateur choisit l’entrée « (éditeur par défaut projet) ».|  
  
 Bien que la vue logique GUID sont extensibles, vous pouvez utiliser uniquement les GUID de vue logique définies dans votre VSPackage.  
  
 Lors de l’arrêt, Visual Studio conserve le GUID de la fabrique d’éditeur et les chaînes d’affichage physique associés à la fenêtre de document afin qu’il peut être utilisé pour ouvrir les fenêtres de document lors de la solution est à nouveau ouvert. Uniquement les fenêtres qui sont ouvertes lors de la fermeture d’une solution sont conservées dans le fichier solution (.suo). Ces valeurs correspondent à la `VSFPROPID_guidEditorType` et `VSFPROPID_pszPhysicalView` valeurs passées dans le `propid` paramètre dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> (méthode).  
  
## <a name="example"></a>Exemple  
 Cet extrait de code illustre comment la <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> objet est utilisé pour accéder à une vue qui implémente `IVsCodeWindow`. Dans ce cas, le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> service sert à appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> et demande `LOGVIEWID_TextView`, qui obtient un pointeur vers un frame de fenêtre. Un pointeur vers l’objet de vue de document est obtenu en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> et en spécifiant une valeur de `VSFPROPID_DocView`. À partir de l’objet de vue de document, `QueryInterface` est appelée pour `IVsCodeWindow`. L’attente est dans ce cas qu’un éditeur de texte est retourné, et par conséquent, l’objet de vue de document renvoyé dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> méthode est une fenêtre de code.  
  
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
 [Prise en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md)   
 [Guide pratique pour Joindre des vues de données de document](../extensibility/how-to-attach-views-to-document-data.md)   
 [Création d’éditeurs et de concepteurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)