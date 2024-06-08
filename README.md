1/
/*Identify the top 5 artists who have produced the most albums?*/

SELEC Artist.Name AS ArtistName,
      COUNT(Track.TrackId) AS TotalTracks
FROM Artist
JOIN Album 
ON Artist.ArtistId = Album.ArtistId
JOIN Track 
ON Album.AlbumId = Track.AlbumId
GROUP BY Artist.ArtistId, Artist.Name
ORDER BY TotalTracks DESC
LIMIT 5;

-------

2/
/*List the total number of tracks recorded by each artist?*/

SELECT Artist.Name, count(Track.Name) Total_of_Track
FROM Artist
JOIN Album
on Artist.ArtistId=Album.ArtistId
JOIN Track
on Track.AlbumId=Album.AlbumId
WHERE Artist.Name In ("Iron Maiden", "Led Zeppelin", "Deep Purple", "Metallica", "U2")
GROUP by 1
ORDER by 2 DESC

-------

3/
/*List the total price of recorded by each Artist?*/

SELECT Artist.Name, sum(Track.UnitPrice) as Price
FROM Artist
JOIN Album
on Artist.ArtistId=Album.ArtistId
JOIN Track
on Track.AlbumId=Album.AlbumId
WHERE Artist.Name In ("Iron Maiden", "Led Zeppelin", "Deep Purple", "Metallica", "U2")
GROUP by 1
ORDER by 2 DESC

-------

4/
/*What is the average duration in milliseconds of tracks from the albums titled "A Matter of Life and Death," "BBC Sessions [Disc 1] [Live]," "MK III The Final Concerts [Disc 1]," "Garage Inc. (Disc 1)," and "Achtung Baby" for each artist?*/

SELECT Artist.Name, avg(Track.Milliseconds) as Avarge_of_Milliseconds
FROM Artist
JOIN Album
on Artist.ArtistId=Album.ArtistId
JOIN Track
on Track.AlbumId=Album.AlbumId
WHERE Artist.Name In ("Iron Maiden", "Led Zeppelin", "Deep Purple", "Metallica", "U2") 
and Album.Title In ("A Matter of Life and Death",
"BBC Sessions [Disc 1] [Live]",
"MK III The Final Concerts [Disc 1]",
"Garage Inc. (Disc 1)",
"Achtung Baby")
GROUP by 1
ORDER by 2 DESC
