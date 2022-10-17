# Oppgave 5 - Visualisering


### a) Høydeprofil
package no.hvl.dat100ptc.oppgave5;

import easygraphics.EasyGraphics;
import no.hvl.dat100ptc.TODO;
import no.hvl.dat100ptc.oppgave1.GPSPoint;
import no.hvl.dat100ptc.oppgave2.GPSData;
import no.hvl.dat100ptc.oppgave2.GPSDataConverter;
import no.hvl.dat100ptc.oppgave2.GPSDataFileReader;
import no.hvl.dat100ptc.oppgave4.GPSComputer;

import javax.swing.JOptionPane;

public class ShowProfile extends EasyGraphics {

	private static final int MARGIN = 50;  // margin on the sides 
	
	private static int MAXBARHEIGHT = 500; // assume no height above 500 meters
	
	private GPSPoint[] gpspoints;

	public ShowProfile() {

		String filename = JOptionPane.showInputDialog("GPS data filnavn: ");
		GPSComputer gpscomputer =  new GPSComputer(filename);

		gpspoints = gpscomputer.getGPSPoints();
		
	}

	public static void main(String[] args) {
		launch(args);
	}

	public void run() {

		int N = gpspoints.length; // number of data points

		makeWindow("Height profile", 2 * MARGIN + 3 * N, 2 * MARGIN + MAXBARHEIGHT);

		// top margin + height of drawing area
		showHeightProfile(MARGIN + MAXBARHEIGHT); 
	}

	public void showHeightProfile(int ybase) {

		// ybase indicates the position on the y-axis where the columns should start
	
		int x = MARGIN,y;

		// TODO - START
		for(int i = 0; i < gpspoints.length; i++) {
			
			double height1 = gpspoints[i].getElevation();
			double høyde1 = Math.round(height1);
			
			setColor(0,0,255);
			drawLine(x, ybase, x, (int)(ybase-høyde1));
			
			x=x+2;
		}
		//throw new UnsupportedOperationException(TODO.method());
	
		// TODO - SLUTT
	}

}

### b) Hastighet

package no.hvl.dat100ptc.oppgave5;

import javax.swing.JOptionPane;

import easygraphics.EasyGraphics;
import no.hvl.dat100ptc.TODO;
import no.hvl.dat100ptc.oppgave1.GPSPoint;
import no.hvl.dat100ptc.oppgave3.GPSUtils;
import no.hvl.dat100ptc.oppgave4.GPSComputer;

public class ShowRoute extends EasyGraphics {

	private static int MARGIN = 50;
	private static int MAPXSIZE = 800;
	private static int MAPYSIZE = 800;

	private GPSPoint[] gpspoints;
	private GPSComputer gpscomputer;
	
	public ShowRoute() {

		String filename = JOptionPane.showInputDialog("GPS data filnavn: ");
		gpscomputer = new GPSComputer(filename);

		gpspoints = gpscomputer.getGPSPoints();

	}

	public static void main(String[] args) {
		launch(args);
	}

	public void run() {

		makeWindow("Route", MAPXSIZE + 2 * MARGIN, MAPYSIZE + 2 * MARGIN);

		showRouteMap(MARGIN + MAPYSIZE);
		
		showStatistics();
	}

	// antall x-pixels per lengdegrad
	public double xstep() {

		double maxlon = GPSUtils.findMax(GPSUtils.getLongitudes(gpspoints));
		double minlon = GPSUtils.findMin(GPSUtils.getLongitudes(gpspoints));

		double xstep = MAPXSIZE / (Math.abs(maxlon - minlon)); 

		return xstep;
	}

	// antall y-pixels per breddegrad
	public double ystep() {
		
	
		double maxlat = GPSUtils.findMax(GPSUtils.getLatitudes(gpspoints));
		double minlat = GPSUtils.findMin(GPSUtils.getLatitudes(gpspoints));
		double ystep = MAPYSIZE / (Math.abs(maxlat - minlat));
		
		// TODO - START
		
		//throw new UnsupportedOperationException(TODO.method());
return ystep;
		// TODO - SLUTT
		
	}

	public void showRouteMap(int ybase) {

		// TODO - START
		double startx = 0;
		double starty = 0;
		double ystep = ystep();
		double xstep = xstep();
		
		double minlat = GPSUtils.findMin(GPSUtils.getLatitudes(gpspoints));
		double minlon = GPSUtils.findMin(GPSUtils.getLongitudes(gpspoints));
		
		starty=ybase-(Math.abs(gpspoints[0].getLatitude()-minlat)*ystep); 
		//Forskjellen nå gange pixler per latitude
		
		startx=50-(Math.abs(gpspoints[0].getLongitude()-minlon)*xstep); 
		//Forskjellen nå gange pixler per logitude
		
		for(int i=1; i < gpspoints.length-1; i++) {
			double lat = gpspoints[i].getLatitude();
			double lon = gpspoints[i].getLongitude();
			double endy = ybase-(Math.abs(lat-minlat)*ystep); 
			double endx = 50+(Math.abs(lon-minlon)*xstep);
			
			setColor(0,255,0);
			drawLine((int)startx,(int)starty,(int)endx,(int)endy);
			fillCircle((int)startx,(int)starty,(int)3);
			starty=endy;
			startx=endx;
			
		}
		
		//throw new UnsupportedOperationException(TODO.method());
		
		// TODO - SLUTT
	}

	public void showStatistics() {

		int TEXTDISTANCE = 20;

		setColor(0,0,0);
		setFont("Courier",12);
		
		String time = ("Total time         : " + GPSUtils.formatTime(gpscomputer.totalTime()));
		drawString(time,TEXTDISTANCE,TEXTDISTANCE);
		String distance = ("Total distance : " + GPSUtils.formatDouble(gpscomputer.totalDistance()/1000)+"km");
		drawString(distance,TEXTDISTANCE,TEXTDISTANCE*2);
		String elevation = ("Total elevation: " + GPSUtils.formatDouble(gpscomputer.totalElevation())+"m");
		drawString(elevation,TEXTDISTANCE,TEXTDISTANCE*3);
		String maxspeed = ("Max Speed      : " + GPSUtils.formatDouble(gpscomputer.maxSpeed())+"km/t");
		drawString(maxspeed,TEXTDISTANCE,TEXTDISTANCE*4);
		String avgspeed = ("Avg Speed      : " + GPSUtils.formatDouble(gpscomputer.averageSpeed())+"km/t");
		drawString(avgspeed,TEXTDISTANCE,TEXTDISTANCE*5);
		String kcal = ("Energy             : " + GPSUtils.formatDouble(gpscomputer.totalKcal(80))+"kcal");
		drawString(kcal,TEXTDISTANCE,TEXTDISTANCE*6);
		// TODO - START
		
		//throw new UnsupportedOperationException(TODO.method());
		
		// TODO - SLUTT;
	}

}

### c) Sykkelruten

package no.hvl.dat100ptc.oppgave5;

import javax.swing.JOptionPane;

import easygraphics.EasyGraphics;
import no.hvl.dat100ptc.TODO;
import no.hvl.dat100ptc.oppgave1.GPSPoint;
import no.hvl.dat100ptc.oppgave2.GPSData;
import no.hvl.dat100ptc.oppgave2.GPSDataFileReader;
import no.hvl.dat100ptc.oppgave3.GPSUtils;
import no.hvl.dat100ptc.oppgave4.GPSComputer;

public class ShowSpeed extends EasyGraphics{
			
	private static final int MARGIN = 50;
	private static final int BARHEIGHT = 200; // assume no speed above 200 km/t

	private GPSComputer gpscomputer;
	private GPSPoint[] gpspoints;
	
	public ShowSpeed() {

		String filename = JOptionPane.showInputDialog("GPS data filnavn: ");
		gpscomputer = new GPSComputer(filename);

		gpspoints = gpscomputer.getGPSPoints();
		
	}
	
	// read in the files and draw into using EasyGraphics
	public static void main(String[] args) {
		launch(args);
	}

	public void run() {

		int N = gpspoints.length-1; // number of data points
		
		makeWindow("Speed profile", 2*MARGIN + 2 * N, 2 * MARGIN + BARHEIGHT);
		
		showSpeedProfile(MARGIN + BARHEIGHT,N);
	}
	
	public void showSpeedProfile(int ybase, int N) {

		// get segments speeds from the GPS computer object		
		double[] speeds = gpscomputer.speeds();
		double avgspeed = 0;
		int x = MARGIN,y;
		
		for(int i = 0; i < gpspoints.length - 1; i++) {
			
			setColor(0,0,255);
			drawLine(x, ybase, x, ybase-(int)speeds[i]);
			
			x=x+2;
			avgspeed = avgspeed+speeds[i];
		}
		 avgspeed = avgspeed/N;
		 setColor(0,255,0);
		 drawLine (MARGIN,ybase-(int)avgspeed,x,ybase-(int)avgspeed);

		// TODO - START
		
		//throw new UnsupportedOperationException(TODO.method());
	
		// TODO - SLUTT
	}
}

