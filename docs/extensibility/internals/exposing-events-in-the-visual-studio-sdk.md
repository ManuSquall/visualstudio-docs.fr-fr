---
title: Exposition d’événements dans le SDK Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7d2eeb155212f7e065febb68b58b31879b5d5a7c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853094"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Exposer des événements dans le SDK Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous permet de la source d’événements à l’aide d’automation. Nous recommandons que vous source d’événements pour les projets et éléments de projet.  
  
 Les événements sont récupérés par les consommateurs d’automation à partir de la <xref:EnvDTE.DTEClass.Events%2A> objet ou <xref:EnvDTE.DTEClass.GetObject%2A> (par exemple, `GetObject("EventObjectName")`). L’environnement appelle `IDispatch::Invoke` à l’aide de la `DISPATCH_METHOD` ou `DISPATCH_PROPERTYGET` indicateurs pour retourner un événement.  
  
 Le processus suivant explique la façon dont les événements spécifiques au VSPackage sont retournés.  
  
1. Démarrage de l’environnement.  
  
2. Il lit à partir du Registre de tous les noms de valeur dans le **Automation**, **AutomationEvents**, et **AutomationProperties** clés de tous les VSPackages et stocke ces noms dans un table.  
  
3. Un utilisateur d’automation appelle, dans cet exemple, `DTE.Events.AutomationProjectsEvents` ou `DTE.Events.AutomationProjectItemsEvents`.  
  
4. L’environnement recherche le paramètre de chaîne dans la table et charge le VSPackage correspondant.  
  
5. L’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode en utilisant le nom passé dans l’appel ; dans cet exemple, `AutomationProjectsEvents` ou `AutomationProjectItemsEvents`.  
  
6. Le package Visual Studio crée un objet racine qui possède des méthodes telles que `get_AutomationProjectsEvents` et `get_AutomationProjectItemEvents` , puis retourne un pointeur IDispatch pour l’objet.  
  
7. L’environnement appelle la méthode appropriée en fonction du nom passé dans l’appel d’automation.  
  
8. Le `get_` méthode crée un autre objet IDispatch d’événements qui implémente à la fois le `IConnectionPointContainer` interface et le `IConnectionPoint` interface et retourne un `IDispatchpointer` à l’objet.  
  
   Pour exposer un événement à l’aide d’automation, vous devez répondre à <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> et de surveiller les chaînes que vous ajoutez au Registre. Dans l’exemple de projet de base, les chaînes sont *BscProjectsEvents* et *BscProjectItemsEvents*.  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Entrées de Registre à partir de l’exemple de projet de base  
 Cette section indique où ajouter les valeurs d’événement automation dans le Registre.  
  
 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]**
  
 **AutomationProjectEvents** = retourne le `AutomationProjectEvents` objet.  
  
 **AutomationProjectItemEvents** = retourne le `AutomationProjectItemsEvents` objet.  
  
|Name|Type|Range|Description|  
|----------|----------|-----------|-----------------|  
|Par défaut (@)|REG_SZ|inutilisé|Non utilisé. Vous pouvez utiliser le champ de données pour la documentation.|  
|*AutomationProjectsEvents*|REG_SZ|Nom de votre objet d’événement.|Il concerne uniquement le nom de clé. Vous pouvez utiliser le champ de données pour la documentation.<br /><br /> Cet exemple provient de l’exemple de projet de base.|  
|*AutomationProjectItemEvents*|REG_SZ|Nom de votre objet d’événement|Il concerne uniquement le nom de clé. Vous pouvez utiliser le champ de données pour la documentation.<br /><br /> Cet exemple provient de l’exemple de projet de base.|  
  
 Quand un de vos objets d’événement sont demandé par un utilisateur d’automation, créer un objet racine qui a des méthodes pour n’importe quel événement prenant en charge votre VSPackage. L’environnement appelle approprié `get_` méthode sur cet objet. Par exemple, si `DTE.Events.AutomationProjectsEvents` est appelée, le `get_AutomationProjectsEvents` méthode est appelée sur l’objet racine.  
  
 ![Événements de projet Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
Modèle Automation pour les événements  
  
 La classe `CProjectEventsContainer` représente l’objet source pour *BscProjectsEvents*, et `CProjectItemsEventsContainer` représente l’objet source pour *BscProjectItemsEvents*.  
  
 Dans la plupart des cas, vous devez retourner un nouvel objet pour chaque requête d’événement, car la plupart des objets événement prennent un objet de filtre. Lorsque vous déclenchez votre événement, vérifiez ce filtre pour vérifier que le Gestionnaire d’événements est appelé.  
  
 *AutomationEvents.h* et *AutomationEvents.cpp* contiennent des déclarations et des implémentations des classes dans le tableau suivant.  
  
|Classe|Description|  
|-----------|-----------------|  
|`CAutomationEvents`|Implémente un objet racine d’événement, extrait du `DTE.Events` objet.|  
|`CProjectsEventsContainer` et `CProjectItemsEventsContainer`|Implémenter les objets de source d’événement qui se déclenchent les événements correspondants.|  
  
 L’exemple de code suivant montre comment répondre à une demande pour un objet d’événement.  
  
```cpp  
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
  
 Dans le code ci-dessus, `g_wszAutomationProjects` est le nom de votre collection de projets (*FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) et `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents* ) sont les noms des événements de projet et les événements qui sont générés à partir de votre implémentation VSPackage d’éléments de projet.  
  
 Objets d’événements sont récupérés à l’emplacement central, le `DTE.Events` objet. De cette façon, tous les objets événements sont regroupés afin qu’un utilisateur final n’a pas à parcourir l’intégralité du modèle objet pour rechercher un événement spécifique. Cela vous permet également de fournir vos objets VSPackage spécifiques, au lieu de vous obliger à implémenter votre propre code pour les événements de l’échelle du système. Toutefois, pour l’utilisateur final, qui doit rechercher un événement pour votre `ProjectItem` interface, il n’est pas immédiatement clair à partir duquel cet objet event est récupéré.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
