---
title: 'Comment : créer des marqueurs de texte personnalisé | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5c44a507cc291b203fc9ba330b248a854f61b81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132260"
---
# <a name="how-to-create-custom-text-markers"></a>Comment : créer des marqueurs de texte personnalisé
Si vous souhaitez créer un marqueur de texte personnalisé pour mettre en évidence ou organiser le code, vous devez effectuer les étapes suivantes :  
  
-   Enregistrer le nouveau marqueur de texte, afin que d’autres outils peuvent y accéder  
  
-   Fournir une implémentation par défaut et une configuration de l’indicateur de texte  
  
-   Créer un service qui peut être utilisé par d’autres processus permettent d’utiliser le marqueur de texte  
  
 Pour plus d’informations sur la façon d’appliquer un marqueur de texte à une région de code, consultez [Comment : utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Pour inscrire un marqueur personnalisé  
  
1.  Créez une entrée de Registre comme suit :  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* \Text Editor\External marqueurs\\*\<MarkerGUID >*  
  
     *\<MarkerGUID >* est un `GUID` utilisé pour identifier le marqueur ajouté  
  
     *\<Version >* est la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par exemple 8.0  
  
     *\<Guid_package >* est le GUID du VSPackage qui implémente l’objet automation.  
  
    > [!NOTE]
    >  Le chemin d’accès racine de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* peut être remplacée par une autre racine lors de l’initialisation de l’interpréteur de commandes de Visual Studio, pour plus d’informations, consultez [Commutateurs de ligne de commande](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2.  Créer les quatre valeurs sous HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* \Text Editor\External marqueurs\\*\<MarkerGUID >*  
  
    -   (Default)  
  
    -   Service  
  
    -   DisplayName  
  
    -   Package  
  
    -   `Default` Cette entrée est facultative de type REG_SZ. Si la valeur, la valeur de l’entrée est une chaîne contenant des informations d’identification utiles, par exemple « Custom marqueur de texte ».  
  
    -   `Service` est une entrée de type REG_SZ contenant la chaîne GUID du service qui fournit le marqueur de texte personnalisé par proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Le format est {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
    -   `DisplayName` est une entrée de type REG_SZ contenant l’ID de ressource du nom de la marque de texte personnalisé. Le format est #YYYY.  
  
    -   `Package` entrée de type REG_SZ contenant le `GUID` de package Visual Studio qui fournit le service répertorié sous le Service. Le format est {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Pour créer un marqueur de texte personnalisé  
  
1.  Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     Votre implémentation de cette interface définit le comportement et l’apparence de votre type de marqueur personnalisée.  
  
     Cette interface est appelée lorsque  
  
    1.  Un utilisateur démarre l’IDE pour la première fois.  
  
    2.  Un utilisateur sélectionne le **paramètres par défaut** sous le **polices et couleurs** page de propriétés de la **environnement** dossier, qui se trouve dans le volet gauche de la  **Options** boîte de dialogue obtenu à partir de la **outils** menu de l’IDE.  
  
2.  Implémentez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> méthode, en spécifiant ce qui `IVsPackageDefinedTextMarkerType` implémentation doit être retournée à selon le GUID spécifié dans l’appel de méthode de type de marqueur.  
  
     L’environnement appelle cette méthode, la première votre type de marqueur personnalisée est créée et spécifie un GUID qui identifie le type de marqueur personnalisée.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Pour mettre en avant votre type de marqueur en tant que service  
  
1.  Appelez le <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> méthode pour <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> est retourné.  
  
2.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> méthode, en spécifiant le GUID d’identification de votre service de type de marqueur personnalisée et un pointeur vers l’implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface. Votre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implémentation doit retourner un pointeur à votre implémentation de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interface.  
  
     Un cookie unique identifiant que votre service est retourné. Vous pouvez utiliser ultérieurement ce cookie révoquer votre service de type de marqueur personnalisée en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> méthode de la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface que vous spécifiez cette valeur de cookie.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de marqueurs de texte avec l’API hérité](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Comment : implémenter des marqueurs d’erreur](../extensibility/how-to-implement-error-markers.md)   
 [Comment : utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)