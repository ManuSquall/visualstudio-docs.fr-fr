---
title: Vues uniques et multiples onglet | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f20e5d251d8d6ef31289fb1b9ee8b9420ff9146a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="single-and-multi-tab-views"></a>Vues uniques et multiples d’onglet
Un éditeur peut créer différents types de vues. Par exemple, une fenêtre d’éditeur de code, un autre est un concepteur de formulaires.  
  
 Une vue dotée de plusieurs onglets est une vue qui comporte plusieurs onglets. Par exemple, l’éditeur HTML comporte deux onglets en bas : **conception** et **Source**, chaque une vue logique. La vue de conception affiche une page web affichée, tandis que l’autre affiche le code HTML qui comprend la page web.  
  
## <a name="accessing-physical-views"></a>L’accès aux affichages physiques  
 Les affichages physiques hébergent des objets de vue de document, représentant chacune une vue de données dans la mémoire tampon, tels que le code ou d’un formulaire. En conséquence, chaque objet de vue de document a un affichage physique (identifiées par un processus appelé une chaîne d’affichage physique) et, en général une vue logique unique.  
  
 Cependant, dans certains cas, une vue physique peut avoir deux ou plusieurs affichages logiques. Un éditeur qui a une fenêtre fractionnée avec des vues côte à côte ou un concepteur de formulaires qui a une vue de conception / l’interface utilisateur graphique et une vue de code-behind-du-formulaire sont des exemples.  
  
 Pour activer votre éditeur afin d’accéder à tous les affichages physiques disponibles, vous devez créer une chaîne d’affichage physique unique pour chaque type d’objet de vue de document que votre fabrique d’éditeur peut créer. Par exemple, le [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] fabrique d’éditeur peut créer le document pour une fenêtre de code et une fenêtre de Concepteur de formulaires, les objets de vue.  
  
## <a name="creating-multi-tabbed-views"></a>Création de vues d’à plusieurs onglets  
 Alors qu’un objet de vue de document doit être associé à une vue physique dans une chaîne d’affichage physique unique, vous pouvez placer plusieurs onglets dans la vue physique pour permettre la consultation des données de différentes façons. Dans cette configuration à plusieurs onglets, tous les onglets sont associés à la même chaîne d’affichage physique, mais chaque onglet est donné à un autre affichage logique GUID.  
  
 Pour créer une vue à plusieurs onglets pour un éditeur, vous devez implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> de l’interface, puis associer un autre affichage logique GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) avec chaque onglet que vous créez.  
  
 L’éditeur HTML de Visual Studio est un exemple d’un éditeur avec une vue de l’onglet multiples. Il a **conception** et **Source** onglets. Pour ce faire, un autre affichage logique est associé à chaque onglet, `LOGICALVIEWID_TextView` pour le **conception** onglet et `LOGICALVIEWID_Code` pour le **Source** onglet.  
  
 En spécifiant la vue logique appropriée, un VSPackage peut accéder à la vue qui correspond à un usage particulier, telles que la création d’un formulaire, de modification de code ou de débogage du code. Toutefois, une fenêtre du doit être identifiée par la chaîne de valeur NULL et que cet attribut doit correspondre à la vue logique principale (`LOGVIEWID_Primary`).  
  
 Le tableau suivant répertorie les valeurs d’affichage logique disponibles et leur utilisation.  
  
|GUID DE LOGVIEWID|Utilisation recommandée|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Vue principal par défaut de la fabrique d’éditeur.<br /><br /> Toutes les fabriques d’éditeur doivent prendre en charge cette valeur. Cette vue doit utiliser la chaîne de valeur NULL en tant que sa chaîne d’affichage physique. Au moins une vue logique doit être définie à cette valeur.|  
|`LOGVIEWID_Debugging`|Affichage de débogage. En règle générale, `LOGVIEWID_Debugging` est mappé à la même vue comme `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Vue lancé par le **afficher le Code** commande.|  
|`LOGVIEWID_Designer`|Vue lancé par le **afficher le formulaire** commande.|  
|`LOGVIEWID_TextView`|Affichage de l’éditeur de texte. C’est la vue retourne <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, à partir de laquelle vous pouvez accéder à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Invite l’utilisateur à choisir la vue à utiliser.|  
|`LOGVIEWID_ProjectSpecificEditor`|Passé par le **ouvrir avec** la boîte de dialogue<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Quand l’utilisateur choisit l’entrée « (éditeur par défaut projet) ».|  
  
 Bien que la vue logique GUID sont extensibles, vous pouvez utiliser uniquement les GUID de vue logique définies dans votre VSPackage.  
  
 Lors de l’arrêt, Visual Studio conserve le GUID de la fabrique d’éditeur et les chaînes d’affichage physique associées à la fenêtre de document afin qu’il peut être utilisé pour ouvrir les fenêtres de document lors de la solution est à nouveau ouvert. Seules les fenêtres qui sont ouverts lors de la fermeture d’une solution sont conservées dans le fichier solution (.suo). Ces valeurs correspondent à la `VSFPROPID_guidEditorType` et `VSFPROPID_pszPhysicalView` les valeurs passées dans les `propid` paramètre dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> (méthode).  
  
## <a name="example"></a>Exemple  
 Cet extrait de code illustre comment la <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> objet est utilisé pour accéder à une vue qui implémente `IVsCodeWindow`. Dans ce cas, le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> service est utilisé pour appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> et demande `LOGVIEWID_TextView`, qui obtient un pointeur vers un frame de fenêtre. Un pointeur vers l’objet de vue de document est obtenu en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> et en spécifiant une valeur de `VSFPROPID_DocView`. À partir de l’objet de vue de document, `QueryInterface` est appelée pour `IVsCodeWindow`. L’attente est dans ce cas qu’un éditeur de texte est retourné et par conséquent, l’objet de vue de document est retourné dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> méthode est une fenêtre de code.  
  
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
 [Prend en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md)   
 [Comment : joindre des vues de données de document](../extensibility/how-to-attach-views-to-document-data.md)   
 [Création d’éditeurs et de concepteurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)