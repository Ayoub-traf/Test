# Test

Patch('Modele PAC Trim'; LookUp('Modele PAC Trim'; ID = ThisItem.ID); {Decision: {Value: "Validé"}; Commentaire: ThisItem.Commentaire; DecidePar: User().Email; DateDecision: Now()});;
Patch(colPAC; ThisItem; {Decision: {Value: "Validé"}; DecidePar: User().Email; DateDecision: Now()});;
Notify("Échantillon validé"; NotificationType.Success)

If(
    IsBlank(ThisItem.Commentaire);
    Notify("Un commentaire est obligatoire pour refuser"; NotificationType.Error);
    Patch('Modele PAC Trim'; LookUp('Modele PAC Trim'; ID = ThisItem.ID); {Decision: {Value: "Refusé"}; Commentaire: ThisItem.Commentaire; DecidePar: User().Email; DateDecision: Now()});;
    Patch(colPAC; ThisItem; {Decision: {Value: "Refusé"}; DecidePar: User().Email; DateDecision: Now()});;
    Notify("Échantillon refusé"; NotificationType.Warning)
)

If(
    IsBlank(ThisItem.Commentaire);
    "Saisir un commentaire";
    Left(ThisItem.Commentaire; 24) & If(Len(ThisItem.Commentaire) > 24; "…"; "")
)
