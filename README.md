# Test

If(
    IsBlank(Coalesce(txtComm.Text; ThisItem.Commentaire));
    Notify("Un commentaire est obligatoire pour refuser"; NotificationType.Error);
    Patch('Modele PAC Trim'; LookUp('Modele PAC Trim'; ID = ThisItem.ID); {Decision: {Value: "Refusé"}; Commentaire: Coalesce(txtComm.Text; ThisItem.Commentaire); DecidePar: User().Email; DateDecision: Now()});;
    Patch(colPAC; ThisItem; {Decision: {Value: "Refusé"}; Commentaire: Coalesce(txtComm.Text; ThisItem.Commentaire); DecidePar: User().Email; DateDecision: Now()});;
    Notify("Échantillon refusé"; NotificationType.Warning)
)


Patch('Modele PAC Trim'; LookUp('Modele PAC Trim'; ID = ThisItem.ID); {Decision: {Value: "Validé"}; Commentaire: Coalesce(txtComm.Text; ThisItem.Commentaire); DecidePar: User().Email; DateDecision: Now()});;
Patch(colPAC; ThisItem; {Decision: {Value: "Validé"}; Commentaire: Coalesce(txtComm.Text; ThisItem.Commentaire); DecidePar: User().Email; DateDecision: Now()});;
Notify("Échantillon validé"; NotificationType.Success)
