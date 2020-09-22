---
title: 'Comment : créer des marqueurs de texte personnalisés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839310"
---
# <a name="how-to-create-custom-text-markers"></a>Guide pratique pour créer des marqueurs de texte personnalisés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous souhaitez créer un marqueur de texte personnalisé pour mettre en évidence ou organiser le code, vous devez effectuer les étapes suivantes :  
  
- Inscrire le nouveau marqueur de texte, afin que d’autres outils puissent y accéder  
  
- Fournir une implémentation et une configuration par défaut du marqueur de texte  
  
- Créer un service qui peut être utilisé par d’autres processus pour utiliser le marqueur de texte  
  
  Pour plus d’informations sur l’application d’un marqueur de texte à une région de code, consultez [Comment : utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Pour inscrire un marqueur personnalisé  
  
1. Créez une entrée de Registre comme suit :  
  
    \\ *\<Version>* Marqueurs HKEY_LOCAL_MACHINE \Software\microsoft\visualstudio \text Editor\External\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID></em>est `GUID` utilisé pour identifier le marqueur ajouté  
  
    *\<Version>* est la version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , par exemple 8,0  
  
    *\<PackageGUID>* GUID du VSPackage qui implémente l’objet Automation.  
  
   > [!NOTE]
   > Le chemin d’accès racine de HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* peut être substitué par une racine secondaire lorsque l’interpréteur de commandes Visual Studio est initialisé. pour plus d’informations, consultez [commutateurs de ligne de commande](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Créer quatre valeurs sous HKEY_LOCAL_MACHINE \\ *\<Version>* marqueurs \Software\microsoft\visualstudio \text Editor\External\\*\<MarkerGUID>*  
  
   - (Par défaut)  
  
   - Service  
  
   - DisplayName  
  
   - Package  
  
   - `Default` est une entrée facultative de type REG_SZ. Lorsque cette valeur est définie, la valeur de l’entrée est une chaîne contenant des informations d’identification utiles, par exemple « marqueur de texte personnalisé ».  
  
   - `Service` est une entrée de type REG_SZ contenant la chaîne GUID du service qui fournit le marqueur de texte personnalisé par proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> . Le format est {XXXXXX XXXX XXXX XXXX XXXXXXXXx}.  
  
   - `DisplayName` est une entrée de type REG_SZ contenant l’ID de ressource du nom du marqueur de texte personnalisé. Le format est #YYYY.  
  
   - `Package` est une entrée de type REG_SZ contenant le `GUID` du VSPackage qui fournit le service indiqué sous service. Le format est {XXXXXX XXXX XXXX XXXX XXXXXXXXx}.  
  
### <a name="to-create-a-custom-text-marker"></a>Pour créer un marqueur de texte personnalisé  
  
1. Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     Votre implémentation de cette interface définit le comportement et l’apparence de votre type de marqueur personnalisé.  
  
     Cette interface est appelée quand  
  
    1. Un utilisateur démarre l’IDE pour la première fois.  
  
    2. Un utilisateur sélectionne le **bouton Réinitialiser les paramètres par défaut** sous la page de propriétés **polices et couleurs** dans le dossier **environnement** , situé dans le volet gauche de la boîte de dialogue **options** obtenue à partir du menu **Outils** de l’IDE.  
  
2. Implémentez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> méthode, en spécifiant l' `IVsPackageDefinedTextMarkerType` implémentation qui doit être retournée en fonction du GUID du type de marqueur spécifié dans l’appel de méthode.  
  
     L’environnement appelle cette méthode la première fois que votre type de marqueur personnalisé est créé, et spécifie un GUID identifiant le type de marqueur personnalisé.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Pour offrir votre type de marqueur en tant que service  
  
1. Appelez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> méthode pour <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> .  
  
     Un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> est retourné.  
  
2. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> méthode, en spécifiant le GUID identifiant votre service de type de marqueur personnalisé et en fournissant un pointeur vers votre implémentation de l' <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface. Votre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implémentation de doit retourner un pointeur vers votre implémentation de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interface.  
  
     Un cookie unique identifiant que votre service est retourné. Vous pouvez utiliser ce cookie ultérieurement pour révoquer votre service de type de marqueur personnalisé en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> méthode de l' <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface spécifiant cette valeur de cookie.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : ajouter des marqueurs de texte standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Comment : implémenter des marqueurs d’erreur](../extensibility/how-to-implement-error-markers.md)   
 [Guide pratique pour utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)
