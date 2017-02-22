---
title: "Vues uniques et multiples d&#39;onglet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), personnalisés - vues uniques et multiples d'onglet"
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Vues uniques et multiples d&#39;onglet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

un éditeur peut créer différents types de vues.  Un exemple est une fenêtre de l'éditeur de code, une autre est le concepteur de formulaires.  
  
 Une vue multi\-avec onglets est une vue avec plusieurs onglets.  Par exemple, l'éditeur HTML deux onglets en bas : **Design** et **Source**, chaque une vue logique.  Le mode Design affiche une page Web affichée, tandis que l'autre affiche le code HTML qui inclut la page Web.  
  
## Vues d'accès physique  
 Objets de vue physiques de document d'hôte de vues, chacun représentant une vue des données dans la mémoire tampon, tel que le code ou un formulaire.  En conséquence, chaque objet de vue du document comprend un point de vue physique \(identifié par un élément appelé une chaîne physique de vue\) et, en général un point de vue logique unique.  
  
 Dans certains cas, bien que, une vue physique peut avoir des vues moins deux logiques.  Certains exemples sont un éditeur qui a une fenêtre fractionnée à côte à côte les vues, ou un concepteur de formulaires avec un point de vue du GUI\/le Design et un point de vue de code\-derrière\-le\-formulaire.  
  
 Pour permettre à votre éditeur d'accéder à toutes les vues disponibles physique, vous devez créer une chaîne unique physique de vue pour chaque type d'objet de vue du document que votre fabrique d'éditeur peut créer.  Par exemple, la fabrique d'éditeur de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] pouvez créer des objets de vue du document pour une fenêtre de code et une fenêtre du concepteur de formulaires.  
  
## Créer des affichages Multi\-Avec Onglets  
 Toutefois un objet de vue du document doit être associé à une vue physique dans une chaîne unique physique de vue, vous pouvez placer plusieurs onglets dans la vue physique pour activer l'affichage des données de différentes façons.  Dans cette configuration multi\-avec onglets, tous les onglets sont associés à la même chaîne physique de vue, mais chaque onglet est fourni une vue logique différente GUID.  
  
 Pour créer une vue multi\-avec tabulations à un éditeur, implémentez l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> puis associez une vue logique différente GUID \(<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>\) avec chaque onglet que vous créez.  
  
 L'éditeur HTML Visual Studio est un exemple d'éditeur d'une vue de multi\-Onglet.  Elle comporte des onglets de **Design** et de **Source** .  Pour cela, une vue logique différente est associée à chaque onglet, `LOGICALVIEWID_TextView` de l'onglet de **Design** et `LOGICALVIEWID_Code` de l'onglet de **Source** .  
  
 En spécifiant la vue logique appropriée, un VSPackage peut accéder à la vue correspondant à un objectif spécifique, tel que concevoir un formulaire, la modification de code, ou le débogage de code.  Toutefois, l'une des fenêtres doit être marquée par la chaîne Null et il doit correspondre à la vue logique principale \(`LOGVIEWID_Primary`\).  
  
 Le tableau suivant répertorie les valeurs logiques disponibles de vue et leur utilisation.  
  
|LOGVIEWID GUID|utilisation recommandée|  
|--------------------|-----------------------------|  
|`LOGVIEWID_Primary`|Valeur par défaut\/mode Principal de fabrique d'éditeur.<br /><br /> toutes les fabriques d'éditeur doivent prendre en charge cette valeur.  cette vue doit utiliser la chaîne Null comme sa chaîne physique de vue.  au moins une vue logique doit être définie à cette valeur.|  
|`LOGVIEWID_Debugging`|Débogage de la vue.  En général, les mappages d' `LOGVIEWID_Debugging` au même s'affichent en tant que `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|vue lancée par la commande d' **Afficher le code** .|  
|`LOGVIEWID_Designer`|Vue lancée par ordre de **formulaire de vue** .|  
|`LOGVIEWID_TextView`|Vue d'édition de texte.  Il s'agit de la vue qui retourne <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, dans laquelle vous pouvez accéder à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Invite l'utilisateur à choisir qui s'affichent à utiliser.|  
|`LOGVIEWID_ProjectSpecificEditor`|Passé par la boîte de dialogue d' **Ouvrir avec** valeur<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> lorsque l'utilisateur choisit « \(éditeur par défaut du projet\) » l'entrée.|  
  
 Bien que la vue logique GUID soient extensible, vous pouvez utiliser uniquement la vue logique GUID défini dans votre VSPackage.  
  
 Lors de l'arrêt, Visual Studio conserve le GUID de la fabrique d'éditeur et les chaînes physiques de vue associées à la fenêtre de document afin qu'il puisse être utilisé pour rouvrir les fenêtres de document lorsque la solution est rouverte.  Seuls les fenêtres ouvertes lorsqu'une solution est fermée sont rendues persistantes dans le fichier solution \(.suo\).  ces valeurs correspondent aux valeurs d' `VSFPROPID_guidEditorType` et d' `VSFPROPID_pszPhysicalView` passées dans le paramètre d' `propid` dans la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> .  
  
## Exemple  
 cet extrait de code montre comment l'objet d' <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> est utilisé pour accéder à une vue qui implémente `IVsCodeWindow`.  Dans ce cas, le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> est utilisé pour appeler l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> et demander `LOGVIEWID_TextView`, qui obtient un pointeur vers un frame de fenêtre.  Pointeur vers l'objet de vue du document est obtenu en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> et en spécifiant une valeur d' `VSFPROPID_DocView`.  De l'objet de vue du document, `QueryInterface` est appelé pour `IVsCodeWindow`.  L'attente est dans ce cas où un éditeur de texte est retourné, et donc l'objet de vue du document retourné dans la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> est une fenêtre de code.  
  
```cpp#  
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
  
## Voir aussi  
 [Prend en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md)   
 [Comment : joindre des vues de données de document](../extensibility/how-to-attach-views-to-document-data.md)   
 [Création de concepteurs et éditeurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)