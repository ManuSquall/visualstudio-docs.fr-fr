---
title: Exposition des événements dans le kit de développement logiciel (SDK) Visual Studio | Microsoft Docs
description: En savoir plus sur les méthodes et les entrées de Registre du kit de développement logiciel Visual Studio qui exposent des événements pour les projets et les éléments de projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99298329b969df3b9d7dbb46a3f4b9e7d4ed7091
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898329"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Exposer des événements dans le kit de développement logiciel Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous permet d’utiliser l’automatisation pour les événements source. Nous vous recommandons d’utiliser des événements source pour les projets et les éléments de projet.

 Les événements sont récupérés par les consommateurs Automation à partir de l' <xref:EnvDTE.DTEClass.Events%2A> objet ou <xref:EnvDTE.DTEClass.GetObject%2A> (par exemple, `GetObject("EventObjectName")` ). L’environnement appelle `IDispatch::Invoke` en utilisant les `DISPATCH_METHOD` `DISPATCH_PROPERTYGET` indicateurs ou pour retourner un événement.

 Le processus suivant explique comment les événements spécifiques au VSPackage sont retournés.

1. L’environnement démarre.

2. Il lit dans le registre tous les noms de valeur sous les clés **Automation**, **AutomationEvents** et **AutomationProperties** de tous les VSPackages, puis stocke ces noms dans une table.

3. Un consommateur Automation appelle, dans cet exemple, `DTE.Events.AutomationProjectsEvents` ou `DTE.Events.AutomationProjectItemsEvents` .

4. L’environnement recherche le paramètre de chaîne dans la table et charge le VSPackage correspondant.

5. L’environnement appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode en utilisant le nom passé dans l’appel ; dans cet exemple, `AutomationProjectsEvents` ou `AutomationProjectItemsEvents` .

6. Le VSPackage crée un objet racine qui a des méthodes telles que `get_AutomationProjectsEvents` et `get_AutomationProjectItemEvents` , puis retourne un pointeur IDispatch à l’objet.

7. L’environnement appelle la méthode appropriée en fonction du nom passé dans l’appel Automation.

8. La `get_` méthode crée un autre objet d’événement IDispatch qui implémente à la fois l' `IConnectionPointContainer` interface et l' `IConnectionPoint` interface et retourne un objet `IDispatchpointer` à l’objet.

   Pour exposer un événement à l’aide d’Automation, vous devez répondre à <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> et surveiller les chaînes que vous ajoutez au registre. Dans l’exemple de projet de base, les chaînes sont *BscProjectsEvents* et *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Entrées de registre de l’exemple de projet de base
 Cette section indique où ajouter des valeurs d’événement Automation au registre.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID \> \AutomationEvents]**

 **AutomationProjectEvents** = retourne l' `AutomationProjectEvents` objet.

 **AutomationProjectItemEvents** = retourne l' `AutomationProjectItemsEvents` objet.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|Valeur par défaut (@)|REG_SZ|Inutilisé|Inutilisé. Vous pouvez utiliser le champ de données pour la documentation.|
|*AutomationProjectsEvents*|REG_SZ|Nom de votre objet d’événement.|Seul le nom de la clé est pertinent. Vous pouvez utiliser le champ de données pour la documentation.<br /><br /> Cet exemple provient de l’exemple de projet de base.|
|*AutomationProjectItemEvents*|REG_SZ|Nom de votre objet d’événement|Seul le nom de la clé est pertinent. Vous pouvez utiliser le champ de données pour la documentation.<br /><br /> Cet exemple provient de l’exemple de projet de base.|

 Lorsque l’un de vos objets d’événement est demandé par un consommateur Automation, créez un objet racine qui possède des méthodes pour tous les événements pris en charge par votre VSPackage. L’environnement appelle la `get_` méthode appropriée sur cet objet. Par exemple, si `DTE.Events.AutomationProjectsEvents` est appelé, la `get_AutomationProjectsEvents` méthode sur l’objet racine est appelée.

 ![Événements de projet Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Modèle Automation pour les événements

 La classe `CProjectEventsContainer` représente l’objet source pour *BscProjectsEvents* et `CProjectItemsEventsContainer` représente l’objet source pour *BscProjectItemsEvents*.

 Dans la plupart des cas, vous devez retourner un nouvel objet pour chaque demande d’événement, car la plupart des objets d’événement prennent un objet de filtre. Lorsque vous déclenchez l’événement, consultez ce filtre pour vérifier que le gestionnaire d’événements est appelé.

 *AutomationEvents. h* et *AutomationEvents. cpp* contiennent des déclarations et des implémentations des classes dans le tableau suivant.

|Classe|Description|
|-----------|-----------------|
|`CAutomationEvents`|Implémente un objet racine d’événement, récupéré à partir de l' `DTE.Events` objet.|
|`CProjectsEventsContainer` et `CProjectItemsEventsContainer`|Implémentez les objets de source d’événements qui déclenchent les événements correspondants.|

 L’exemple de code suivant montre comment répondre à une demande d’objet d’événement.

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

 Dans le code ci-dessus, `g_wszAutomationProjects` est le nom de votre collection de projets (*FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) et `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) sont les noms des événements de projet et des événements d’éléments de projet qui proviennent de votre implémentation du VSPackage.

 Les objets d’événement sont récupérés à partir du même emplacement central, l' `DTE.Events` objet. De cette façon, tous les objets d’événement sont regroupés afin qu’un utilisateur final n’ait pas à parcourir l’ensemble du modèle objet pour trouver un événement spécifique. Cela vous permet également de fournir vos objets VSPackage spécifiques, au lieu de vous obliger à implémenter votre propre code pour les événements au niveau du système. Toutefois, pour l’utilisateur final, qui doit trouver un événement pour votre `ProjectItem` interface, il n’est pas immédiatement clair à partir de l’emplacement où cet objet d’événement est récupéré.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
