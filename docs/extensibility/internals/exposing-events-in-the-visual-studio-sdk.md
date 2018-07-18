---
title: Exposant les événements dans le Kit de développement logiciel de Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 02ddcf0c2321f6f4c07170117c6474b993c340f4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132232"
---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>Exposant les événements dans le Kit de développement logiciel de Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permet à la source d’événements à l’aide d’automation. Il est recommandé que vous source d’événements pour les projets et éléments de projet.  
  
 Les événements sont récupérés par les consommateurs d’automation à partir de la <xref:EnvDTE.DTEClass.Events%2A> objet ou <xref:EnvDTE.DTEClass.GetObject%2A> (« EventObjectName »). L’environnement appelle `IDispatch::Invoke` à l’aide de la `DISPATCH_METHOD` ou `DISPATCH_PROPERTYGET` indicateurs pour retourner un événement.  
  
 La procédure suivante explique comment les événements de VSPackage spécifique sont retournés.  
  
1.  Démarrage de l’environnement.  
  
2.  Il lit à partir du Registre de tous les noms de valeur sous les clés d’automatisation, AutomationEvents et AutomationProperties de tous les VSPackages et stocke ces noms dans une table.  
  
3.  Un consommateur automation appelle, dans cet exemple, `DTE.Events.AutomationProjectsEvents` ou `DTE.Events.AutomationProjectItemsEvents`.  
  
4.  L’environnement de recherche le paramètre de chaîne de la table et charge le VSPackage correspondant.  
  
5.  L’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> passés à la méthode en utilisant le nom de l’appel ; dans cet exemple, AutomationProjectsEvents ou AutomationProjectItemsEvents.  
  
6.  Le VSPackage crée un objet racine qui a des méthodes telles que `get_AutomationProjectsEvents` et `get_AutomationProjectItemEvents` , puis retourne un pointeur IDispatch pour l’objet.  
  
7.  L’environnement appelle la méthode appropriée en fonction du nom passé dans l’appel d’automation.  
  
8.  Le `get_` méthode crée un autre objet IDispatch d’événements qui implémente à la fois le `IConnectionPointContainer` interface et `IConnectionPoint` interface et retourne un IDispatchpointer à l’objet.  
  
 Pour exposer un événement à l’aide d’automation, vous devez répondre à <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> et de surveiller les chaînes que vous ajoutez au Registre. Dans l’exemple de projet de base, les chaînes sont « BscProjectsEvents » et « BscProjectItemsEvents ».  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Entrées de Registre de l’exemple de projet de base  
 Cette section montre où ajouter les valeurs d’événement automation dans le Registre.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 « AutomationProjectEvents « = » de retourne l’objet AutomationProjectEvents »  
  
 « AutomationProjectItemEvents « = » de retourne l’objet AutomationProjectItemsEvents »  
  
|Name|Type|Range|Description|  
|----------|----------|-----------|-----------------|  
|Par défaut (@)|REG_SZ|Non utilisé|Non utilisé. Vous pouvez utiliser le champ de données pour la documentation.|  
|AutomationProjectsEvents|REG_SZ|Nom de votre objet d’événement.|Il concerne uniquement le nom de clé. Vous pouvez utiliser le champ de données pour la documentation.<br /><br /> Cet exemple provient de l’exemple de projet de base.|  
|AutomationProjectItemEvents|REG_SZ|Nom de votre objet d’événement|Il concerne uniquement le nom de clé. Vous pouvez utiliser le champ de données pour la documentation.<br /><br /> Cet exemple provient de l’exemple de projet de base.|  
  
 Lorsqu’un de vos objets d’événement sont demandé par un consommateur d’automation, créer un objet racine qui a des méthodes pour tout événement qui prend en charge de votre VSPackage. L’environnement appelle approprié `get_` méthode sur cet objet. Par exemple, si `DTE.Events.AutomationProjectsEvents` est appelée, la `get_AutomationProjectsEvents` méthode est appelée sur l’objet racine.  
  
 ![Événements de projet Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
Modèle Automation pour les événements  
  
 La classe `CProjectEventsContainer` représente l’objet source pour BscProjectsEvents, tandis que `CProjectItemsEventsContainer` représente l’objet source pour BscProjectItemsEvents.  
  
 Dans la plupart des cas, vous devez retourner un objet pour chaque demande de l’événement étant donné que la plupart des objets d’événements prennent un objet de filtre. Lorsque vous déclenchez l’événement, vérifiez ce filtre pour vérifier que le Gestionnaire d’événements est appelé.  
  
 AutomationEvents.h et AutomationEvents.cpp contiennent les déclarations et des implémentations des classes dans le tableau suivant.  
  
|Classe|Description|  
|-----------|-----------------|  
|`CAutomationEvents`|Implémente un objet racine d’événement, extrait du `DTE.Events` objet.|  
|`CProjectsEventsContainer` et `CProjectItemsEventsContainer`|Implémenter les objets de source d’événements qui déclenchent les événements correspondants.|  
  
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
  
 Dans le code ci-dessus, `g_wszAutomationProjects` est le nom de votre collection de projets (« FigProjects »), `g_wszAutomationProjectsEvents` (« FigProjectsEvents ») et `g_wszAutomationProjectItemsEvents` (« FigProjectItemEvents ») sont les noms des événements dans les projets et éléments de projet des événements qui sont générés à partir de votre Implémentation du VSPackage.  
  
 Objets d’événements sont récupérés à l’emplacement central, le `DTE.Events` objet. De cette manière, tous les objets événements sont regroupés afin qu’un utilisateur final n’a pas à parcourir le modèle d’objet complet pour rechercher un événement spécifique. Cela vous permet également de fournir vos objets VSPackage spécifiques, au lieu de vous demander d’implémenter votre propre code pour des événements système. Toutefois, pour l’utilisateur final, qui doit rechercher un événement pour votre `ProjectItem` interface, il n’est pas immédiatement clair à partir duquel cet objet d’événement est récupéré.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [Exemples d’extensibilité Visual Studio](http://aka.ms/vs2015sdksamples)