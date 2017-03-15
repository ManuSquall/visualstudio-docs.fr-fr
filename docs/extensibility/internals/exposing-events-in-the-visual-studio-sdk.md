---
title: "Exposition d’&#233;v&#233;nements dans le Kit de d&#233;veloppement Logiciel de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "événements (Visual Studio), exposant"
  - "Automation (Visual Studio SDK), exposant des événements"
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Exposition d’&#233;v&#233;nements dans le Kit de d&#233;veloppement Logiciel de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous permet de vous émettent des événements à l’aide d’automation. Nous recommandons que vous source d’événements pour les projets et éléments de projet.  
  
 Les événements sont récupérés par les consommateurs de l’automation à partir de la <xref:EnvDTE.DTEClass.Events%2A> objet ou <xref:EnvDTE.DTEClass.GetObject%2A> (« EventObjectName »). L’environnement appelle `IDispatch::Invoke` à l’aide de la `DISPATCH_METHOD` ou `DISPATCH_PROPERTYGET` indicateurs pour retourner un événement.  
  
 La procédure suivante explique comment les événements VSPackage spécifiques sont retournées.  
  
1.  Démarrage de l’environnement.  
  
2.  Il lit le Registre de tous les noms de valeur dans les clés d’automatisation, AutomationEvents et AutomationProperties de tous les packages VS et stocke ces noms dans une table.  
  
3.  Un client automation appelle, dans cet exemple, `DTE.Events.AutomationProjectsEvents` ou `DTE.Events.AutomationProjectItemsEvents`.  
  
4.  L’environnement de recherche le paramètre de chaîne de la table et charge le VSPackage correspondant.  
  
5.  L’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> transmis à la méthode en utilisant le nom de l’appel ; dans cet exemple, AutomationProjectsEvents ou AutomationProjectItemsEvents.  
  
6.  Le VSPackage crée un objet racine qui possède des méthodes telles que `get_AutomationProjectsEvents` et `get_AutomationProjectItemEvents` puis retourne un pointeur IDispatch vers l’objet.  
  
7.  L’environnement appelle la méthode appropriée en fonction du nom passé dans l’appel d’automation.  
  
8.  Le `get_` méthode crée un autre objet IDispatch d’événements qui implémente à la fois le `IConnectionPointContainer` interface et `IConnectionPoint` interface et retourne un IDispatchpointer à l’objet.  
  
 Pour exposer un événement à l’aide d’automation, vous devez répondre à <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> et de surveiller les chaînes que vous ajoutez au Registre. Dans l’exemple de projet de base, les chaînes sont « BscProjectsEvents » et « BscProjectItemsEvents ».  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Entrées de Registre à partir de l’exemple de projet de base  
 Cette section indique où ajouter les valeurs des événements automation dans le Registre.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 « AutomationProjectEvents » = » de renvoie l’objet AutomationProjectEvents »  
  
 « AutomationProjectItemEvents » = » de renvoie l’objet AutomationProjectItemsEvents »  
  
|Nom|Type|Plage|Description|  
|----------|----------|-----------|-----------------|  
|Par défaut (@)|REG_SZ|Inutilisé|Inutilisé. Vous pouvez utiliser le champ de données pour la documentation.|  
|AutomationProjectsEvents|REG_SZ|Nom de votre objet d’événement.|Il concerne uniquement le nom de clé. Vous pouvez utiliser le champ de données pour la documentation.<br /><br /> Cet exemple provient de l’exemple de projet de base.|  
|AutomationProjectItemEvents|REG_SZ|Nom de votre objet d’événement|Il concerne uniquement le nom de clé. Vous pouvez utiliser le champ de données pour la documentation.<br /><br /> Cet exemple provient de l’exemple de projet de base.|  
  
 Lorsqu’un de vos objets événement sont demandé par un client automation, créer un objet racine qui a des méthodes pour n’importe quel événement prenant en charge votre VSPackage. L’environnement appelle approprié `get_` méthode sur cet objet. Par exemple, si `DTE.Events.AutomationProjectsEvents` est appelée, la `get_AutomationProjectsEvents` méthode est appelée sur l’objet racine.  
  
 ![Événements de projet Visual Studio](../../extensibility/internals/media/projectevents.png "ProjectEvents")  
Modèle Automation pour les événements  
  
 La classe `CProjectEventsContainer` représente l’objet source pour BscProjectsEvents, tandis que `CProjectItemsEventsContainer` représente l’objet source pour BscProjectItemsEvents.  
  
 Dans la plupart des cas, vous devez retourner un nouvel objet pour chaque demande d’événement, car la plupart des objets événement prennent un objet de filtre. Lorsque vous déclenchez votre événement, vérifiez ce filtre pour vérifier que le Gestionnaire d’événements est appelé.  
  
 AutomationEvents.h et AutomationEvents.cpp contiennent des déclarations et des implémentations des classes dans le tableau suivant.  
  
|Classe|Description|  
|-----------|-----------------|  
|`CAutomationEvents`|Implémente un objet racine d’événement, extrait du `DTE.Events` objet.|  
|`CProjectsEventsContainer` et `CProjectItemsEventsContainer`|Implémentez les objets source d’événements qui déclenchent les événements correspondants.|  
  
 L’exemple de code suivant montre comment répondre à une demande pour un objet d’événement.  
  
```cpp#  
STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
{  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)   
        //Is the requested name our Projects object?  
    {  
        return GetAutomationProjects(ppIDispatch);  
        // Gets our Projects object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        //Is the requested name our ProjectsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectEvents object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectItemsEvents object.  
    }  
    return E_INVALIDARG;  
}  
```  
  
 Dans le code ci-dessus, `g_wszAutomationProjects` est le nom de votre collection de projets (« FigProjects »), `g_wszAutomationProjectsEvents` (« FigProjectsEvents ») et `g_wszAutomationProjectItemsEvents` (« FigProjectItemEvents ») sont les noms des événements de projet et les événements qui sont générés à partir de votre implémentation VSPackage d’éléments de projet.  
  
 Les objets d’événements sont récupérés à l’emplacement central, le `DTE.Events` objet. De cette façon, tous les objets événements sont regroupés afin qu’un utilisateur final n’a pas à parcourir l’intégralité du modèle objet pour rechercher un événement spécifique. Cela vous permet également de fournir vos objets VSPackage spécifiques, au lieu d’avoir à implémenter votre propre code pour des événements système. Toutefois, pour l’utilisateur final, qui doit rechercher un événement pour votre `ProjectItem` interface, il n’est pas immédiatement évident dans laquelle cet objet event est récupéré.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [Exemples VSSDK](../../misc/vssdk-samples.md)