---
title: 'Procédure : Créer des marqueurs de texte personnalisé | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1c8389788504a49bc9a4962c89ed47500a1dc7da
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965218"
---
# <a name="how-to-create-custom-text-markers"></a>Procédure : Créer des marqueurs de texte personnalisé
Si vous souhaitez créer un marqueur de texte personnalisé pour mettre en évidence ou organiser le code, vous devez procédez comme suit :  
  
- Inscrire le nouveau marqueur de texte, afin que les autres outils puissent y accéder.  
  
- Fournir une implémentation par défaut et la configuration du marqueur de texte.  
  
- Créer un service qui peut être utilisé par d’autres processus s’utilisent le marqueur de texte.  
  
  Pour plus d’informations sur la façon d’appliquer un marqueur de texte dans une région de code, consultez [Comment : Utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md).  
  
## <a name="to-register-a-custom-marker"></a>Pour inscrire un marqueur personnalisé  
  
1. Créez une entrée de Registre comme suit :  
  
    **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\<Version > \Text Editor\External marqueurs\\\<MarkerGUID >**  
  
    *\<MarkerGUID >* est un `GUID` utilisé pour identifier le marqueur en cours d’ajout  
  
    `<Version>` est la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par exemple 8.0  
  
    `<PackageGUID>` le GUID du VSPackage implémente l’objet automation.  
  
   > [!NOTE]
   >  Le chemin d’accès racine de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\<Version >** peut être remplacée par une autre racine lors de l’initialisation de l’interpréteur de commandes de Visual Studio, pour plus d’informations, consultez [Commutateurs de ligne de commande](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Créez quatre valeurs sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\<Version > \Text Editor\External marqueurs\\\<MarkerGUID >**  
  
   -   (Default)  
  
   -   Service  
  
   -   DisplayName  
  
   -   Package  
  
   -   `Default` Cette entrée est facultative de type REG_SZ. Lorsque la valeur, la valeur de l’entrée est une chaîne contenant des informations d’identification utiles, par exemple « Custom marqueur de texte ».  
  
   -   `Service` est une entrée de type REG_SZ contenant la chaîne GUID du service qui fournit le marqueur de texte personnalisé par proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Le format est {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
   -   `DisplayName` est une entrée de type REG_SZ contenant l’ID de ressource du nom du marqueur de texte personnalisé. Le format est #YYYY.  
  
   -   `Package` entrée de type REG_SZ contenant le `GUID` du VSPackage qui fournit le service répertorié sous le Service. Le format est {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
## <a name="to-create-a-custom-text-marker"></a>Pour créer un marqueur de texte personnalisé  
  
1.  Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     Votre implémentation de cette interface définit le comportement et l’apparence de votre type de marqueur personnalisé.  
  
     Cette interface est appelée lorsque  
  
    1.  Un utilisateur démarre l’IDE pour la première fois.  
  
    2.  Un utilisateur sélectionne le **paramètres par défaut** bouton sous le **polices et couleurs** page de propriétés dans le **environnement** dossier, situé dans le volet gauche de la  **Options** boîte de dialogue obtenu à partir de la **outils** menu de l’IDE.  
  
2.  Implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> méthode, en spécifiant ce qui `IVsPackageDefinedTextMarkerType` implémentation doit être retournée en fonction sur le type de marqueur GUID spécifié dans l’appel de méthode.  
  
     L’environnement appelle cette fois le premier (méthode), votre type de marqueur personnalisé est créé et spécifie un GUID qui identifie le type de marqueur personnalisé.  
  
## <a name="to-proffer-your-marker-type-as-a-service"></a>Présentation de votre type de marqueur en tant que service  
  
1.  Appelez le <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> méthode pour <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> est retourné.  
  
2.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> méthode, en spécifiant le GUID d’identification de votre service de type de marqueur personnalisé et un pointeur vers votre implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface. Votre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implémentation doit retourner un pointeur à votre implémentation de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interface.  
  
     Un cookie unique identifiant que votre service est retourné. Vous pouvez utiliser ultérieurement ce cookie pour révoquer votre service de type de marqueur personnalisé en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> méthode de la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface en spécifiant cette valeur de cookie.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Guide pratique pour Ajouter des marqueurs de texte standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Guide pratique pour Implémenter des marqueurs d’erreur](../extensibility/how-to-implement-error-markers.md)   
 [Guide pratique pour Utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)