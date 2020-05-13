---
title: Exposer les événements dans le studio visuel SDK (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48f1e0ea0dcd07bbc26fc89d5c61a6a5941d4727
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708485"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Exposer les événements dans le Studio Visuel SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]vous permet de vous procurer des événements en utilisant l’automatisation. Nous vous recommandons de vous procurer des événements pour des projets et des éléments de projet.

 Les événements sont récupérés <xref:EnvDTE.DTEClass.Events%2A> par <xref:EnvDTE.DTEClass.GetObject%2A> les consommateurs `GetObject("EventObjectName")`d’automatisation de l’objet ou (par exemple, ). L’environnement `IDispatch::Invoke` appelle `DISPATCH_METHOD` en `DISPATCH_PROPERTYGET` utilisant le ou les drapeaux pour retourner un événement.

 Le processus suivant explique comment les événements spécifiques à VSPackage sont retournés.

1. L’environnement commence.

2. Il lit à partir du registre tous les noms de valeur sous **l’automatisation**, **AutomationEvents**, et **AutomationProperties** clés de tous les VSPackages, et stocke ces noms dans une table.

3. Un consommateur d’automatisation appelle, dans cet exemple, `DTE.Events.AutomationProjectsEvents` ou `DTE.Events.AutomationProjectItemsEvents`.

4. L’environnement trouve le paramètre de chaîne dans la table et charge le VSPackage correspondant.

5. L’environnement <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> appelle la méthode en utilisant le nom passé dans l’appel; dans cet `AutomationProjectsEvents` exemple, ou `AutomationProjectItemsEvents`.

6. Le VSPackage crée un objet racine `get_AutomationProjectsEvents` `get_AutomationProjectItemEvents` qui a des méthodes telles que et retourne ensuite un pointeur IDispatch à l’objet.

7. L’environnement appelle la méthode appropriée basée sur le nom passé dans l’appel d’automatisation.

8. La `get_` méthode crée un autre objet d’événement basé `IConnectionPointContainer` sur `IConnectionPoint` IDispatch `IDispatchpointer` qui implémente à la fois l’interface et l’interface et renvoie un objet.

   Pour exposer un événement en utilisant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> l’automatisation, vous devez répondre et surveiller les chaînes que vous ajoutez au registre. Dans l’échantillon basic Project, les cordes sont *BscProjectsEvents* et *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Inscriptions au registre de l’échantillon du projet de base
 Cette section indique où ajouter les valeurs d’événements d’automatisation au registre.

 **[HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-8.0-Packages\\<PkgGUID\>-AutomationEvents]**

 **AutomationProjectEvents** - `AutomationProjectEvents` Retourne l’objet.

 **AutomationProjectItemEvents** - `AutomationProjectItemsEvents` Retourne l’objet.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|Par défaut ()|REG_SZ|Inutilisé|Inutilisé. Vous pouvez utiliser le champ de données pour la documentation.|
|*AutomationProjectsEvents*|REG_SZ|Nom de votre objet événementiel.|Seul le nom clé est pertinent. Vous pouvez utiliser le champ de données pour la documentation.<br /><br /> Cet exemple provient de l’échantillon du projet de base.|
|*AutomationProjectItemEvents*|REG_SZ|Nom de votre objet événementiel|Seul le nom clé est pertinent. Vous pouvez utiliser le champ de données pour la documentation.<br /><br /> Cet exemple provient de l’échantillon du projet de base.|

 Lorsque l’un de vos objets d’événement est demandé par un consommateur d’automatisation, créez un objet racine qui a des méthodes pour tout événement que votre VSPackage prend en charge. L’environnement appelle `get_` la méthode appropriée sur cet objet. Par exemple, `DTE.Events.AutomationProjectsEvents` si on `get_AutomationProjectsEvents` l’appelle, la méthode de l’objet racine est invoquée.

 ![Événements du projet Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjetEvents") Modèle d’automatisation pour les événements

 La `CProjectEventsContainer` classe représente l’objet source de *BscProjectsEvents*, et `CProjectItemsEventsContainer` représente l’objet source de *BscProjectItemsEvents*.

 Dans la plupart des cas, vous devez retourner un nouvel objet pour chaque demande d’événement parce que la plupart des objets événementiels prennent un objet de filtre. Lorsque vous allumez votre événement, vérifiez ce filtre pour vérifier que le gestionnaire d’événements est appelé.

 *AutomationEvents.h* et *AutomationEvents.cpp* contiennent des déclarations et des implémentations des classes dans le tableau suivant.

|Classe|Description|
|-----------|-----------------|
|`CAutomationEvents`|Implémente un objet racine `DTE.Events` d’événement, récupéré de l’objet.|
|`CProjectsEventsContainer` et `CProjectItemsEventsContainer`|Implémenter les objets source de l’événement qui tirent les événements correspondants.|

 L’exemple de code suivant montre comment répondre à une demande d’objet événementiel.

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

 Dans le code `g_wszAutomationProjects` ci-dessus, est le nom de `g_wszAutomationProjectsEvents` votre collection de projets `g_wszAutomationProjectItemsEvents` (*FigProjects*), (*FigProjectsEvents*) et (*FigProjectItemEvents*) sont les noms des événements de projet et des éléments de projet qui proviennent de votre mise en œuvre VSPackage.

 Les objets de l’événement sont `DTE.Events` récupérés à partir du même emplacement central, l’objet. De cette façon, tous les objets d’événement sont regroupés de sorte qu’un utilisateur final n’a pas à parcourir l’ensemble du modèle d’objet pour trouver un événement spécifique. Cela vous permet également de fournir vos objets VSPackage spécifiques, au lieu de vous obliger à implémenter votre propre code pour les événements à l’échelle du système. Toutefois, pour l’utilisateur final, qui `ProjectItem` doit trouver un événement pour votre interface, il n’est pas immédiatement clair de l’endroit où cet objet d’événement est récupéré.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
