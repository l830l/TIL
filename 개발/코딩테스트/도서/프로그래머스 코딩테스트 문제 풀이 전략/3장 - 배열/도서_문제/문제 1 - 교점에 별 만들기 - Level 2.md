# 문제 링크
- https://school.programmers.co.kr/learn/courses/30/lessons/87377
# 의사코드
1. Line 클래스 생성 - x의 계수, y의 계수, 상수항
2. Point 클래스 생성 - x 좌표, y 좌표
3. Line 클래스 입력 값에 따라
	1. Line 클래스를 만들어 리스트에 넣는다.
	2. 기존 Line 들과 비교하여 교점이 있으면 교점을 계산한다
		1. 일단 해당 교점이 x,y 의 최솟값 또는 최댓값이니 계산한다.
		2. set 에 넣어준다.
4. 해당 좌표의 x,y 최댓값 최솟값을 이용하여 . 을 찍어준다.
5. 교점 Set 을 이용하여 교점 부분에 \*를 찍어준다
# 예상 시간 복잡도
O(N^2 + WH)
# 내 코드
``` java
import java.util.*;

class Line{
    long nx;
    long ny;
    long c;

    Line (long nx, long ny, long c) {
        this.nx = nx;
        this.ny = ny;
        this.c = c;
    }
}

class Point {
    long x;
    long y;

    Point (long x, long y) {
        this.x = x;
        this.y = y;
    }
}

class Solution {
    List<Line> lineList = new ArrayList<>();
    Set<Point> pointSet = new HashSet<>();
    ArrayList<StringBuilder> result = new ArrayList<>();
    Long minCrossX;
    Long minCrossY;
    Long maxCrossX;
    Long maxCrossY;

    public String[] solution(int[][] lines) {
        for (int[] line : lines) {
            Line newLine = new Line(line[0], line[1], line[2]);
            lineList.stream().map(oldLine -> getCrossPoint(oldLine, newLine))
                    .filter(Objects::nonNull)
                    .forEach(point -> {
                        crossMinMax(point);
                        pointSet.add(point);
                    });
            lineList.add(newLine);
        }

        for(long i = minCrossY; i <= maxCrossY; i++) {
            StringBuilder sb = new StringBuilder();
            for(long j = minCrossX; j <= maxCrossX; j++) {
                sb.append('.');
            }
            result.add(sb);
        }
        pointSet.forEach(point -> {
            result.get((int)(result.size() - (point.y - minCrossY) - 1)).setCharAt((int)(point.x - minCrossX), '*');
        });

        return result.stream().map(StringBuilder::toString).toArray(String[]::new);
    }

    private Point getCrossPoint(Line oldLine, Line newLine) {
        long denominator = oldLine.nx * newLine.ny - oldLine.ny * newLine.nx;
        if(denominator == 0) return null;

        long numeratorX = oldLine.ny * newLine.c - oldLine.c * newLine.ny;
        if(numeratorX % denominator != 0) return null;

        long numeratorY = oldLine.c * newLine.nx - oldLine.nx * newLine.c;
        if(numeratorY % denominator != 0) return null;

        return new Point(numeratorX / denominator, numeratorY / denominator);
    }

    private void crossMinMax(Point point){
        if(minCrossX == null || point.x < minCrossX) minCrossX = point.x;
        if(minCrossY == null || point.y < minCrossY) minCrossY = point.y;
        if(maxCrossX == null || point.x > maxCrossX) maxCrossX = point.x;
        if(maxCrossY == null || point.y > maxCrossY) maxCrossY = point.y;
    }
}
```
# 개선 코드

