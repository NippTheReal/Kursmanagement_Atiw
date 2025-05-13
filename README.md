# Kursmanagement_Atiw

SQL Statements für SWD:

Kursteilnehmer Tabelle anlegen:

CREATE TABLE teilnehmer_{kursname} (
	Teilehmer_ID int,
	Kurs_ID int,
	Member_ID int,
	PRIMARY KEY (Teilehmer_ID),
	FOREIGN KEY (Kurs_ID) REFERENCES Kurse(Kurs_ID),
	FOREIGN KEY (Member_ID) REFERENCES Kurse(Member_ID),
);

for (int i = 0; i < max-anzahl; i++){
	INSERT INTO teilnehmer_{kursname} (Teilehmer_ID) VALUES ({i});
};	


Kurse anlegen:

INSERT INTO courses (spaltennamen) REFERENCES (werte aus Textfeldern);

Räume ausgeben lassen:

SELECT room_ID FROM rooms;

Test ob Belegt:

SELECT r.room_ID
        FROM rooms r
        WHERE NOT EXISTS (
            SELECT 1
            FROM reservations res
            WHERE res.room_ID = r.room_ID
              AND TO_TIMESTAMP(:beginn, 'YYYY-MM-DD HH24:MI:SS') < res.reservierungsende
              AND TO_TIMESTAMP(:beginn, 'YYYY-MM-DD HH24:MI:SS') + NUMTODSINTERVAL(:dauer, 'MINUTE') > res.reservierungsbeginn
        );
