---
title: "Comment&#160;: cr&#233;er des marqueurs de texte personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - marqueurs de texte personnalisé"
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Comment&#160;: cr&#233;er des marqueurs de texte personnalis&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous souhaitez créer un marqueur de texte personnalisé pour mettre en évidence ou organiser le code, vous devez effectuer les opérations suivantes :  
  
-   Enregistrer le nouveau marqueur de texte, afin que d’autres outils peuvent y accéder  
  
-   Fournir une implémentation par défaut et la configuration de l’indicateur de texte  
  
-   Créer un service qui peut être utilisé par d’autres processus s’utiliser de marqueur de texte  
  
 Pour plus d’informations sur la façon d’appliquer un marqueur de texte à une région de code, consultez [Comment : utiliser les marqueurs de texte](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Pour inscrire un marqueur personnalisé  
  
1.  Créez une entrée de Registre comme suit :  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\< Version>*\Text Editor\External marqueurs\\*\< MarkerGUID>*  
  
     *\< MarkerGUID>*est un `GUID` utilisé pour identifier le marqueur en cours d’ajout  
  
     *\< version>* est la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par exemple 8.0  
  
     *\< PackageGUID>* est le GUID du package VS qui implémente l’objet automation.  
  
    > [!NOTE]
    >  Le chemin d’accès racine de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\< Version>* peut être remplacée par une autre racine lors de l’initialisation de l’interpréteur de commandes de Visual Studio, pour plus d’informations, consultez [les commutateurs de ligne de commande](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2.  Créez quatre valeurs sous HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\< Version>*\Text Editor\External marqueurs\\*\< MarkerGUID>*  
  
    -   (Default)  
  
    -   Service  
  
    -   DisplayName  
  
    -   Package  
  
    -   `Default` Cette entrée est facultative de type REG_SZ. Lorsque la valeur, la valeur de l’entrée est une chaîne contenant des informations d’identification utiles, par exemple « Custom marqueur de texte ».  
  
    -   `Service` est une entrée de type REG_SZ contenant la chaîne GUID du service qui fournit le marqueur de texte personnalisé par proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Le format est {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
    -   `DisplayName` est une entrée de type REG_SZ contenant l’ID de ressource du nom de marqueur de texte personnalisé. Le format est #YYYY.  
  
    -   `Package` entrée de type REG_SZ contenant le `GUID` d’un VSPackage qui fournit le service répertorié sous le Service. Le format est {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Pour créer un marqueur de texte personnalisé  
  
1.  Implémentez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interface.  
  
     Votre implémentation de cette interface définit le comportement et l’apparence de votre type de marqueur personnalisée.  
  
     Cette interface est appelée lorsque  
  
    1.  Un utilisateur démarre l’IDE pour la première fois.  
  
    2.  Un utilisateur sélectionne le **paramètres par défaut** bouton sous le **polices et couleurs** page de propriétés de la **environnement** dossier, situé dans le volet gauche de la **Options** provenant de la boîte de dialogue le **outils** menu de l’IDE.  
  
2.  Implémentez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> méthode, en spécifiant ce qui `IVsPackageDefinedTextMarkerType` implémentation doit être retournée selon le type de marqueur GUID spécifié dans l’appel de méthode.  
  
     L’environnement appelle cette fois le premier (méthode), votre type de marqueur personnalisée est créée et spécifie un GUID qui identifie le type de marqueur personnalisée.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Pour mettre en avant votre type de marqueur en tant que service  
  
1.  Appelez le <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> méthode pour <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> est retourné.  
  
2.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> méthode, en spécifiant le GUID d’identification de votre service de type de marqueur personnalisée et un pointeur vers l’implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface. Votre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implémentation doit retourner un pointeur à votre implémentation de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interface.  
  
     Un cookie unique qui identifie que votre service est retourné. Vous pouvez utiliser ultérieurement ce cookie révoquer votre service de type de marqueur personnalisée en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> Procédé de la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface spécifiant cette valeur de cookie.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Comment : implémenter des marqueurs d’erreur](../extensibility/how-to-implement-error-markers.md)   
 [Comment : utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)